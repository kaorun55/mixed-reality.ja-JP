---
title: 目の視線入力とコミット
description: 目の視線入力とコミットの入力モデルの概要
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 視線追跡, Mixed Reality, 入力, 目の視線入力, 目のターゲット設定, HoloLens 2, 視線に基づく選択
ms.openlocfilehash: 89f5031635f2b67ba4c9afdf605559c2b9da4ac2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437828"
---
# <a name="eye-gaze-and-commit"></a><span data-ttu-id="2cbc0-104">目の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2cbc0-104">Eye-gaze and commit</span></span>
<span data-ttu-id="2cbc0-105">_目の視線入力とコミット_は、[視線入力とコミット](gaze-and-commit.md)入力モデルの特殊なケースです。これには、見つめるだけでオブジェクトをターゲットにし、手のジェスチャ、音声コマンド、周辺入力機器 (ゲーム コントローラーなど) などのセカンダリ _コミット_入力を使用してそのオブジェクトを操作することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-105">_Eye-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object by simply looking at it and then acting on it with a secondary _commit_ input, such as a hand gesture, voice command or peripheral input (e.g., game controller).</span></span> 

<span data-ttu-id="2cbc0-106">HoloLens 2 では、頭の視線入力ではなく目の視線入力を使用することで_視線入力とコミット_をより迅速で快適なものにできます。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-106">With HoloLens 2, we have the great opportunity to make _gaze and commit_ faster and more comfortable by using eye-gaze instead of head-gaze.</span></span> <span data-ttu-id="2cbc0-107">これにより、一般的な[頭の視線入力とコミット](gaze-and-commit.md)の相互作用モデルを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-107">This allows to extend the common [head-gaze and commit](gaze-and-commit.md) interaction model:</span></span> 
1. <span data-ttu-id="2cbc0-108">ターゲットを見つめるだけ</span><span class="sxs-lookup"><span data-stu-id="2cbc0-108">Simply look at a target and</span></span> 
2. <span data-ttu-id="2cbc0-109">ターゲットを選択するという意図を示すために、次のような第 2 の明示的な入力を実行します。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-109">To confirm your intention to select the target, perform a secondary explicit input such as a:</span></span>  
   - <span data-ttu-id="2cbc0-110">手のジェスチャ (エアタップなど)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-110">Hand gesture (e.g., an Air Tap)</span></span>
   - <span data-ttu-id="2cbc0-111">ボタン押下 (Bluetooth キーボードやクリッカーなど)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-111">Button press (e.g., on a Bluetooth keyboard or clicker)</span></span>
   - <span data-ttu-id="2cbc0-112">音声コマンド (「選択」など)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-112">Voice command (e.g., "Select")</span></span>
   - <span data-ttu-id="2cbc0-113">ドウェル (つまり、ユーザーはターゲットを見つめ続けることで選択する)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-113">Dwelling (i.e., the user simply keeps looking at the target to select)</span></span>

<span data-ttu-id="2cbc0-114">ただし、目の視線入力はいくつかの点で頭の視線入力とまったく異なる動作をするため、さまざまな固有の課題があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-114">However, eye gaze behaves very differently to head gaze in certain ways and hence comes with a number of unique challenges.</span></span> <span data-ttu-id="2cbc0-115">[目の視線入力設計ガイドライン](eye-tracking.md)に、ホログラフィック アプリで視線追跡を入力として使用する場合に考慮すべき一般的なメリットと課題の概要が記載されています。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-115">In the [Eye Gaze Design Guidelines](eye-tracking.md), we summarize general advantages and challenges to take into account when using eye tracking as an input in your holographic app.</span></span> <span data-ttu-id="2cbc0-116">このセクションでは、_目の視線入力とコミット_に関する特定の設計考慮事項を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-116">In this section, we focus on the specific design considerations for _eye-gaze and commit_.</span></span>
<span data-ttu-id="2cbc0-117">まず、私たちの目は非常に速く動くため、視界からすばやくターゲット設定を行うのに適しています。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-117">First, our eyes move incredibly fast and thus are great at quickly targeting across the view.</span></span> <span data-ttu-id="2cbc0-118">したがって、目の視線入力は、特に、エアタップやボタン押下などの高速コミットと組み合わせたときに、迅速な視線入力とコミットのアクションに理想的と言えます。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-118">This makes eye-gaze ideal for quick gaze-and-commit actions especially when combined with fast commits such as an air tap or button press.</span></span>
   
<span data-ttu-id="2cbc0-119">ここでは、この種の相互作用に目の視線入力を使用する場合の設計ガイドラインを示し、頭の視線入力と目の視線入力の違いについて考慮しておく必要がある点を説明します。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-119">In the following, we will address design guidelines when using eye-gaze for this type of interaction and will discuss differences between head- and eye-gaze that you should keep in mind.</span></span>

## <a name="design-guidelines-for-eye-gaze-and-commit"></a><span data-ttu-id="2cbc0-120">目の視線入力とコミットに関する設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="2cbc0-120">Design guidelines for eye-gaze and commit</span></span>

<span data-ttu-id="2cbc0-121">**カーソルを表示しない**:頭の視線入力の使用中はカーソルを使わずに操作するのはほぼ不可能なのに対して、目の視線入力の使用中はカーソルがたちまち集中の邪魔をしたり、目障りになったりします。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-121">**Do not show a cursor**: While it is nearly impossible to interact without a cursor when using head gaze, the cursor becomes quickly distracting and annoying when using eye gaze.</span></span> <span data-ttu-id="2cbc0-122">視線追跡が機能しているかどうかということと、現在見ているターゲットが正しく検出されたかどうかをユーザーに知らせるためにカーソルに頼るのではなく、繊細なビジュアル ハイライトを使用します (詳細については後述します)。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-122">Instead of relying on a cursor to inform the user whether eye tracking is working and has correctly detected the currently looked at target, use subtle visual highlights (more details below).</span></span>

<span data-ttu-id="2cbc0-123">**繊細なブレンド ホバー フィードバックを追求する**:頭の視線入力にとっては優れた視覚的フィードバックが、目の視線入力にとっては不快で混乱するエクスペリエンスになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-123">**Strive for subtle blended hover feedback**: What seems great visual feedback for head gaze can result in terrible, overwhelming experiences using eye gaze.</span></span> <span data-ttu-id="2cbc0-124">目の動きは非常に速いため、視野の中の点から点へとすばやく動くことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-124">Remember that your eyes are enormously fast, quickly darting across points in your field-of-view.</span></span> <span data-ttu-id="2cbc0-125">周りを見回しているときに急にハイライトが変化 (オン/オフ) すると、フィードバックがちらつく可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-125">Quick sudden highlight changes (on/off) may result in flickery feedback when looking around.</span></span> <span data-ttu-id="2cbc0-126">そのため、ホバー フィードバックを提供する場合は、スムーズ ブレンドイン ハイライト (視線を外す場合はスムーズ ブレンドアウト ハイライト) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-126">So, when providing hover feedback, we recommend using a smoothly blended-in highlight (and blended-out when looking away).</span></span> <span data-ttu-id="2cbc0-127">これは、ターゲットを見たときに、最初はフィードバックにほとんど気付かないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-127">This means that at first you would barely notice the feedback when looking at a target.</span></span> <span data-ttu-id="2cbc0-128">500 - 1000 ミリ秒かけて、ハイライトの輝度が上がります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-128">Over the course of 500-1000 ms the highlight would increase in intensity.</span></span> <span data-ttu-id="2cbc0-129">初級ユーザーは見つめているターゲットが正しく判別されたことを確かめようとしてターゲットを見つめ続けるかもしれませんが、上級ユーザーはフィードバックが最大輝度になるのを待たずにすばやく視線入力とコミットを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-129">While novice users could keep looking at the target to ensure that the system has correctly determined the focused target, expert users could quickly gaze-and-commit without waiting until the feedback is at its full intensity.</span></span> <span data-ttu-id="2cbc0-130">加えて、ホバー フィードバックをフェードアウトするときにブレンドアウトを使用することもお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-130">In addition, we also recommend using a blend-out when fading out the hover feedback.</span></span> <span data-ttu-id="2cbc0-131">調査により、周辺視野 (自分が注視していない視野領域) では動きやコントラストの急激な変化に気付きやすいことがわかりました。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-131">Research has shown that quick motions and contrast changes are very noticeable in your peripheral vision (the area of your visual field where you are not looking).</span></span>
<span data-ttu-id="2cbc0-132">フェードアウトをブレンドインと同じほど遅くする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-132">The fade-out doesn't have to be as slow as the blend-in.</span></span> <span data-ttu-id="2cbc0-133">このことは、ハイライトのコントラストが高い場合や色が変化する場合にのみ重要です。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-133">This is only critical when you have high contrast or color changes for your highlight.</span></span> <span data-ttu-id="2cbc0-134">ホバー フィードバックが極めて繊細な場合は、初めは違いに気付かないかもしれません。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-134">If the hover feedback was pretty subtle to begin with, you probably won't notice a difference.</span></span>

<span data-ttu-id="2cbc0-135">**視線入力とコミット信号を同期させるよう配慮する**:入力信号の同期は、単純なエア タップやボタン押下の場合は大きな問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-135">**Look out for synchronizing gaze and commit signals**: The synchronization of input signals may be less of a challenge for simple air taps and button presses.</span></span> <span data-ttu-id="2cbc0-136">長い音声コマンドや複雑な手のジェスチャが必要になる可能性のある、より複雑なコミット アクションを使用する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-136">It is something to look out for in case you want to use more complicated commit actions that may involve long voice commands or complicated hand gestures.</span></span> <span data-ttu-id="2cbc0-137">ターゲットを見つめて、長い音声コマンドを発音する場合を想像してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-137">Imagine you look at a target and utter a long voice command.</span></span> <span data-ttu-id="2cbc0-138">発音するのに必要な時間と、発音された内容をシステムが検出するのに必要な時間を考えると、目の視線入力はシーン内の離れた場所にある新しいターゲットに移動している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-138">Taken into account the time that you need to say it and the time that the system needed to detect what you said, your eye gaze has usually long moved on to some new target in the scene.</span></span> <span data-ttu-id="2cbc0-139">そのため、コマンドが認識されるまでターゲットを見つめ続けなければならないことをユーザーに気付かせるか、コマンドの開始とユーザーがその時点で見ていたものを特定するという方法で入力を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc0-139">Hence, either make your users aware that they may need to keep looking at a target until the command has been recognized or handle the input in a way to determine the onset of the command and what the user had been looking at back then.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cbc0-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cbc0-140">See also</span></span>
* <span data-ttu-id="2cbc0-141">[視線ベースの操作] (eye-gaze-interaction.md)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-141">[Eye-based interaction] (eye-gaze-interaction.md)</span></span>
* <span data-ttu-id="2cbc0-142">[HoloLens 2 上の視線追跡] (eye-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2cbc0-142">[Eye tracking on HoloLens 2] (eye-tracking.md)</span></span>
* [<span data-ttu-id="2cbc0-143">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2cbc0-143">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2cbc0-144">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="2cbc0-144">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="2cbc0-145">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="2cbc0-145">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2cbc0-146">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2cbc0-146">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2cbc0-147">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="2cbc0-147">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2cbc0-148">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="2cbc0-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2cbc0-149">音声入力</span><span class="sxs-lookup"><span data-stu-id="2cbc0-149">Voice input</span></span>](voice-input.md)