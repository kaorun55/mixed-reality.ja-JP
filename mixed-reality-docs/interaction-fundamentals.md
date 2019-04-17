---
title: 相互作用の基礎
description: HoloLens の間で構築したエクスペリエンス (第 1 世代) HoloLens 2、イマーシブ ヘッドセットを共有すると便利ですが見つかりましたいくつを書き留めるが開始されました。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 複合現実との対話を設計します。
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597551"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="26a09-104">相互作用の基礎</span><span class="sxs-lookup"><span data-stu-id="26a09-104">Interaction fundamentals</span></span>

<span data-ttu-id="26a09-105">HoloLens とイマーシブ ヘッドセットの間でエクスペリエンスを構築したら、下の点を共有すると便利ですが見つかりましたを書き始めたしました。</span><span class="sxs-lookup"><span data-stu-id="26a09-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="26a09-106">複合現実対話デザインの基本的な構成要素の役割も果たします。</span><span class="sxs-lookup"><span data-stu-id="26a09-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="26a09-107">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="26a09-107">Device support</span></span>

<span data-ttu-id="26a09-108">適用される使用可能な相互作用デザイン記事と、どのデバイスの種類または種類の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26a09-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="26a09-109"><strong>入力</strong></span><span class="sxs-lookup"><span data-stu-id="26a09-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="26a09-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="26a09-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-112"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="26a09-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="26a09-113"><a href="gestures.md">関節手</a></span><span class="sxs-lookup"><span data-stu-id="26a09-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="26a09-114">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="26a09-115"><a href="gaze-targeting.md">監視対象とします。</a></span><span class="sxs-lookup"><span data-stu-id="26a09-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="26a09-116">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="26a09-117"><a href="gaze-targeting.md">視線の先を対象とします。</a></span><span class="sxs-lookup"><span data-stu-id="26a09-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-118">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-119">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-120">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="26a09-121"><a href="gestures.md">ジェスチャ</a></span><span class="sxs-lookup"><span data-stu-id="26a09-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-122">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-123">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="26a09-124"><a href="voice-design.md">音声のデザイン</a></span><span class="sxs-lookup"><span data-stu-id="26a09-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-125">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-126">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-127">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="26a09-128">ゲームパッド</span><span class="sxs-lookup"><span data-stu-id="26a09-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-129">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-130">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-131">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="26a09-132"><a href="motion-controllers.md">アニメーション コント ローラー</a></span><span class="sxs-lookup"><span data-stu-id="26a09-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="26a09-133">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="26a09-134"><strong>概念と空間機能</strong></span><span class="sxs-lookup"><span data-stu-id="26a09-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-135"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="26a09-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="26a09-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="26a09-137"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="26a09-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="26a09-138"><a href="spatial-sound-design.md">サウンドの空間の設計</a></span><span class="sxs-lookup"><span data-stu-id="26a09-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-139">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-140">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-141">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="26a09-142"><a href="spatial-mapping-design.md">空間マッピングの設計</a></span><span class="sxs-lookup"><span data-stu-id="26a09-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-143">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-144">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="26a09-145"><a href="hologram.md">ホログラム</a></span><span class="sxs-lookup"><span data-stu-id="26a09-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-146">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="26a09-147">✔️</span><span class="sxs-lookup"><span data-stu-id="26a09-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="26a09-148">ユーザーは、カメラです。</span><span class="sxs-lookup"><span data-stu-id="26a09-148">The user is the camera</span></span>

![ユーザーは、カメラです。](images/useriscamera-640px.jpg)

<span data-ttu-id="26a09-150">に関する彼らの実数部と仮想世界に移動する場合に、ユーザーの観点の設計について常に考えます。</span><span class="sxs-lookup"><span data-stu-id="26a09-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="26a09-151">**一般的な質問**</span><span class="sxs-lookup"><span data-stu-id="26a09-151">**Some questions to ask**</span></span>
* <span data-ttu-id="26a09-152">ユーザーに座って、リクライニングであること、または徒歩、エクスペリエンスを使用しているときにしますか。</span><span class="sxs-lookup"><span data-stu-id="26a09-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="26a09-153">コンテンツは、別の位置にどのように調整しますか。</span><span class="sxs-lookup"><span data-stu-id="26a09-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="26a09-154">ユーザー調整できますか。</span><span class="sxs-lookup"><span data-stu-id="26a09-154">Can the user adjust it?</span></span>
* <span data-ttu-id="26a09-155">ユーザーが快適にアプリを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="26a09-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="26a09-156">**ベスト プラクティス**</span><span class="sxs-lookup"><span data-stu-id="26a09-156">**Best practices**</span></span>
* <span data-ttu-id="26a09-157">ユーザーは、カメラであり、動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="26a09-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="26a09-158">ドライブにできるようにします。</span><span class="sxs-lookup"><span data-stu-id="26a09-158">Let them drive.</span></span>
* <span data-ttu-id="26a09-159">事実上、ユーザーを転送する必要がある場合は、不安を合わせた前庭に関する問題を機密性が高いものです。</span><span class="sxs-lookup"><span data-stu-id="26a09-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="26a09-160">短いアニメーションを使用して、</span><span class="sxs-lookup"><span data-stu-id="26a09-160">Use shorter animations</span></span>
* <span data-ttu-id="26a09-161">ダウン/左/右からアニメーション化する、または Z の代わりにフェードイン</span><span class="sxs-lookup"><span data-stu-id="26a09-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="26a09-162">低下するタイミング</span><span class="sxs-lookup"><span data-stu-id="26a09-162">Slow down timing</span></span>
* <span data-ttu-id="26a09-163">バック グラウンドで世界を表示します。</span><span class="sxs-lookup"><span data-stu-id="26a09-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="26a09-164">**避けるべきこと**</span><span class="sxs-lookup"><span data-stu-id="26a09-164">**What to avoid**</span></span>
* <span data-ttu-id="26a09-165">シェイク、カメラまたは 3DOF を意図的にロックしないでください (方向、翻訳のみ)、ユーザーが感じたことができます。</span><span class="sxs-lookup"><span data-stu-id="26a09-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="26a09-166">突然動きがありません。</span><span class="sxs-lookup"><span data-stu-id="26a09-166">No abrupt movement.</span></span> <span data-ttu-id="26a09-167">ユーザーとの間にコンテンツを表示する必要がある場合、緩やかに変化かつ円滑目標の移動最大快適性します。</span><span class="sxs-lookup"><span data-stu-id="26a09-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="26a09-168">ユーザーは、それらに送信される大規模なメニューに対応します。</span><span class="sxs-lookup"><span data-stu-id="26a09-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="26a09-169">高速化、またはユーザーのカメラを有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="26a09-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="26a09-170">ユーザーは、機密性の高い (angular と直線) の高速化します。</span><span class="sxs-lookup"><span data-stu-id="26a09-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="26a09-171">ユーザーの視点を活用します。</span><span class="sxs-lookup"><span data-stu-id="26a09-171">Leverage the user's perspective</span></span>

<span data-ttu-id="26a09-172">ユーザーは、没入型および holographic デバイス ディスプレイでの複合現実の世界を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26a09-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="26a09-173">この表示が呼び出された、HoloLens、 [holographic フレーム](holographic-frame.md)します。</span><span class="sxs-lookup"><span data-stu-id="26a09-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="26a09-174">2D の開発では、頻繁にアクセスされるコンテンツと設定を簡単にアクセスできるようにするための画面の隅に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="26a09-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="26a09-175">ただし、holographic のアプリでコンテンツをユーザーのビューの隅にない可能性がありますアクセスします。</span><span class="sxs-lookup"><span data-stu-id="26a09-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="26a09-176">ここでは、holographic のフレームの中央には、コンテンツの主な場所です。</span><span class="sxs-lookup"><span data-stu-id="26a09-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="26a09-177">ユーザーは、重要なイベントまたは即時表示外にあるオブジェクトを見つけやすいように説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a09-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="26a09-178">矢印、ライトの証跡、文字ヘッドの移動、吹き出し、ポインター、空間のサウンド、および音声プロンプトを使用して、アプリで重要なコンテンツをユーザーに役立つことができます。</span><span class="sxs-lookup"><span data-stu-id="26a09-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="26a09-179">ユーザーの快適性のために画面ロック コンテンツではなくすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="26a09-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="26a09-180">ビュー内のコンテンツを保管する必要がある場合、世界中に配置および"tag-along"[スタート] メニューのようなコンテンツを作成します。</span><span class="sxs-lookup"><span data-stu-id="26a09-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="26a09-181">ユーザーの観点とプルのコンテンツは、環境で自然に感じられます。</span><span class="sxs-lookup"><span data-stu-id="26a09-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="26a09-182">![フレームの端に達すると、ユーザーのビューに依存して、[スタート] メニュー](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="26a09-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="26a09-183">*フレームの端に達すると、ユーザーのビューに依存して、[スタート] メニュー*</span><span class="sxs-lookup"><span data-stu-id="26a09-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="26a09-184">これらがカットしないため、holographic フレーム内に収まる場合に、HoloLens ホログラムを実際と思われます。</span><span class="sxs-lookup"><span data-stu-id="26a09-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="26a09-185">ユーザーは、フレーム内のホログラムの境界を確認するために移動します。</span><span class="sxs-lookup"><span data-stu-id="26a09-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="26a09-186">HoloLens には、ユーザーのビュー内に収まるし、メイン アクションで、フォーカスを保持するように UI を簡略化する重要です。</span><span class="sxs-lookup"><span data-stu-id="26a09-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="26a09-187">イマーシブ ヘッドセットがデバイスのビューのフィールド内の永続的な仮想世界の錯覚を維持するために重要です。</span><span class="sxs-lookup"><span data-stu-id="26a09-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="26a09-188">快適性</span><span class="sxs-lookup"><span data-stu-id="26a09-188">User comfort</span></span>

<span data-ttu-id="26a09-189">最大値を確実に[快適性](comfort.md)ヘッド マウントのディスプレイでは作成し、人間が 3D 図形と自然にオブジェクトの相対位置を解釈する方法を模倣した方法でコンテンツを表示するには、設計者や開発者にとって重要です世界です。</span><span class="sxs-lookup"><span data-stu-id="26a09-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="26a09-190">物理の観点からも重要です首部分の腕疲れるモーションが不要なコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="26a09-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="26a09-191">HoloLens のイマーシブ ヘッドセットを開発するかどうかが両方の目のビジュアルを表示するために重要です。</span><span class="sxs-lookup"><span data-stu-id="26a09-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="26a09-192">1 つ目のヘッドアップ ディスプレイをレンダリングのみによりにくくインターフェイスについては、ユーザーの目、脳に uneasiness の原因とします。</span><span class="sxs-lookup"><span data-stu-id="26a09-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="26a09-193">体験を共有します。</span><span class="sxs-lookup"><span data-stu-id="26a09-193">Share your experience</span></span>

<span data-ttu-id="26a09-194">使用して[実際のキャプチャを混合](mixed-reality-capture.md)ユーザーが写真や、いつでもエクスペリエンスのビデオをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="26a09-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="26a09-195">スナップショットまたはビデオをお勧めする必要のあるアプリでのエクスペリエンスを検討してください。</span><span class="sxs-lookup"><span data-stu-id="26a09-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="26a09-196">Windows Mixed Reality ホームの基本的な UI 要素を活用します。</span><span class="sxs-lookup"><span data-stu-id="26a09-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="26a09-197">Windows PC エクスペリエンスがデスクトップで始まるよう Windows Mixed Reality ホームから始まります。</span><span class="sxs-lookup"><span data-stu-id="26a09-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="26a09-198">[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)を理解し、3 D の場所を移動します。 本質的な能力を活用します。</span><span class="sxs-lookup"><span data-stu-id="26a09-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="26a09-199">HoloLens、自宅は、実際の場所です。</span><span class="sxs-lookup"><span data-stu-id="26a09-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="26a09-200">イマーシブ ヘッドセット、自宅は仮想の場所です。</span><span class="sxs-lookup"><span data-stu-id="26a09-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="26a09-201">自宅は、[スタート] メニューを開き、アプリやコンテンツを配置に使用する場所もです。</span><span class="sxs-lookup"><span data-stu-id="26a09-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="26a09-202">複合現実のコンテンツを自宅に入力し、同時に複数のアプリを使用して、マルチタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="26a09-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="26a09-203">自宅に配置することは、デバイスを再起動する場合でも、ままです。</span><span class="sxs-lookup"><span data-stu-id="26a09-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="26a09-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="26a09-204">See also</span></span>
* [<span data-ttu-id="26a09-205">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="26a09-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="26a09-206">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="26a09-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="26a09-207">音声のデザイン</span><span class="sxs-lookup"><span data-stu-id="26a09-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="26a09-208">アニメーション コント ローラー</span><span class="sxs-lookup"><span data-stu-id="26a09-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="26a09-209">サウンドの空間の設計</span><span class="sxs-lookup"><span data-stu-id="26a09-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="26a09-210">空間マッピングの設計</span><span class="sxs-lookup"><span data-stu-id="26a09-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="26a09-211">快適性</span><span class="sxs-lookup"><span data-stu-id="26a09-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="26a09-212">Windows Mixed Reality ホームに移動します。</span><span class="sxs-lookup"><span data-stu-id="26a09-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
