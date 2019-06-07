---
title: アプリの品質基準
description: このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリの品質基準、実際には、混合 mixed reality アプリ
ms.openlocfilehash: dfa1390190fad8d84982171dfbcfa101b20501dc
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750320"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="b41c6-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-104">App quality criteria</span></span>

<span data-ttu-id="b41c6-105">このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="b41c6-106">次の情報を提供する各要素について</span><span class="sxs-lookup"><span data-stu-id="b41c6-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="b41c6-107">概要 – の品質要因と重要な理由の簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="b41c6-108">デバイスによる影響 - Mixed Reality をウィンドウのデバイスの種類は影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="b41c6-109">品質基準 – の品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="b41c6-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="b41c6-110">– メソッドに、問題を計測 (またはエクスペリエンス) を測定する方法。</span><span class="sxs-lookup"><span data-stu-id="b41c6-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="b41c6-111">推奨事項のより優れたユーザー エクスペリエンスを提供する方法の概要。</span><span class="sxs-lookup"><span data-stu-id="b41c6-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="b41c6-112">リソース-関連する開発者とアプリのより優れたエクスペリエンスを作成すると便利であるデザイン リソース</span><span class="sxs-lookup"><span data-stu-id="b41c6-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="b41c6-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="b41c6-113">Frame rate</span></span>

<span data-ttu-id="b41c6-114">フレーム レートはホログラムの安定性とユーザーの快適性の最初の柱です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="b41c6-115">推奨されるターゲットの下のフレーム レートには、ホログラムちらついたり、エクスペリエンスの信憑性に悪影響を与えると、目の疲労が発生する可能性を表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="b41c6-116">Windows Mixed Reality イマーシブ ヘッドセットでのユーザー エクスペリエンスのターゲット フレーム レートは、60 Hz またはサポートする Windows Mixed Reality 互換性のある Pc に応じて 90 Hz のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="b41c6-117">HoloLens 先のフレーム レートは 60 Hz です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-121">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-121">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-122">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-123">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-124">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-124">Best</span></span>  |  <span data-ttu-id="b41c6-125">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-125">Meets</span></span> |  <span data-ttu-id="b41c6-126">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="b41c6-127">アプリでは、一貫してターゲット デバイスの 2 つ目の (FPS) 目標あたりのフレーム数を満たしています。HoloLens; に 60 fps90 超 Pc; fpsメイン ストリームの Pc で 60 fps します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="b41c6-128">アプリは、コア エクスペリエンスを妨げていない断続的なフレームのドロップまたは、FPS は一貫して目標より低いが、アプリのエクスペリエンスを妨げるありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="b41c6-129">アプリには、フレーム レートの平均が 10 秒ごとに以下のドロップが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b41c6-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-130">How to measure</span></span>

* <span data-ttu-id="b41c6-131">リアルタイムのフレーム レートのグラフがを通じてによって提供される、 [Windows Device Portal](using-the-windows-device-portal.md#system-performance) 「システムのパフォーマンス」の下。</span><span class="sxs-lookup"><span data-stu-id="b41c6-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="b41c6-132">開発のデバッグには、アプリにフレーム レートの診断カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="b41c6-133">サンプルのカウンターは、リソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="b41c6-134">フレーム レートの低下は、頭を左右に移動することによって、アプリの実行中に、デバイスで発生することができます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="b41c6-135">ホログラムちらつく移動の予期しない場合は、フレーム レートが低い、または安定性の面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-136">Recommendations</span></span>

* <span data-ttu-id="b41c6-137">開発作業の開始時に、フレーム レート カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="b41c6-138">フレーム レートの低下が発生する変更を評価して、パフォーマンス バグとして適切に解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-139">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-140">Documentation</span></span>

* [<span data-ttu-id="b41c6-141">複合現実のパフォーマンスを理解</span><span class="sxs-lookup"><span data-stu-id="b41c6-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="b41c6-142">ホログラム安定性とフレーム レート</span><span class="sxs-lookup"><span data-stu-id="b41c6-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="b41c6-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="b41c6-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="b41c6-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-145">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-146">MRToolkit、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="b41c6-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="b41c6-147">MRToolkit、シェーダー</span><span class="sxs-lookup"><span data-stu-id="b41c6-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="b41c6-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="b41c6-148">External references</span></span>

* [<span data-ttu-id="b41c6-149">Unity では、モバイル アプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="b41c6-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="b41c6-150">ホログラム安定性</span><span class="sxs-lookup"><span data-stu-id="b41c6-150">Hologram stability</span></span>

<span data-ttu-id="b41c6-151">安定したホログラムは、使いやすさと、アプリの信憑性を向上し、ユーザーの使いやすい表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="b41c6-152">ホログラム安定性の品質が適切なアプリの開発と (追跡) を理解するデバイスの機能の結果をその環境。</span><span class="sxs-lookup"><span data-stu-id="b41c6-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="b41c6-153">フレーム レートが安定性の最初の柱の中、その他の要因の安定性を含む影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="b41c6-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="b41c6-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="b41c6-155">空間アンカーまでの距離</span><span class="sxs-lookup"><span data-stu-id="b41c6-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="b41c6-156">Tracking</span><span class="sxs-lookup"><span data-stu-id="b41c6-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-159"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-160">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-160">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-161">❌</span><span class="sxs-lookup"><span data-stu-id="b41c6-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-162">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-162">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-163">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-163">Best</span></span>  |  <span data-ttu-id="b41c6-164">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-164">Meets</span></span> |  <span data-ttu-id="b41c6-165">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-166">ホログラムが一貫して安定したが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="b41c6-167">セカンダリのコンテンツは予期しない動きです。または、予期しない動きが全体的なアプリ エクスペリエンスを妨げるありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="b41c6-168">フレームで主要なコンテンツには、予期せぬ動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-169">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-169">How to measure</span></span>

<span data-ttu-id="b41c6-170">While ソックスを着けずに、デバイスと、エクスペリエンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="b41c6-171">サイド バイ サイドに頭を移動、ホログラムが予期しない動きを表示する場合、フレーム レートが低いまたは焦点面に安定性の面の不適切なアラインメントは考えられる原因になります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="b41c6-172">ホログラムや環境を移動、スイムレーンと jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="b41c6-173">この種類のアニメーションは、空間アンカーに環境、または距離を追跡しないデバイスによる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="b41c6-174">大規模な場合、または複数ホログラムがフレームでは、安定化平面に起因揺れの可能性がありますが表示された場合、並列で、ヘッドの位置を移動中に、さまざまな深さでホログラム動作を観察します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="b41c6-175">Recomendations</span><span class="sxs-lookup"><span data-stu-id="b41c6-175">Recomendations</span></span>

* <span data-ttu-id="b41c6-176">開発作業の開始時、フレーム レート カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="b41c6-177">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="b41c6-178">常に、アンカーの 3 つのメートル単位でアンカー ホログラムをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="b41c6-179">環境の適切な追跡のためのセットアップを確認します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="b41c6-180">フレーム内でさまざまな焦点の深さのレベルでホログラムを回避するために、エクスペリエンスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-181">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-182">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-182">Documentation</span></span>

* [<span data-ttu-id="b41c6-183">ホログラム安定性とフレーム レート</span><span class="sxs-lookup"><span data-stu-id="b41c6-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="b41c6-184">安定化平面を使用して、ケース スタディ</span><span class="sxs-lookup"><span data-stu-id="b41c6-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="b41c6-185">複合現実のパフォーマンスを理解</span><span class="sxs-lookup"><span data-stu-id="b41c6-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="b41c6-186">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="b41c6-187">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="b41c6-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="b41c6-188">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="b41c6-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="b41c6-189">フレームの静止した基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-190">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-190">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-191">MR コンパニオン キット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="b41c6-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="b41c6-192">実際の画面上の位置をホログラム</span><span class="sxs-lookup"><span data-stu-id="b41c6-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="b41c6-193">物理オブジェクト相互の関連配置するためのもの) であればホログラムのずれは、ホログラムと実際の非結合の明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="b41c6-194">配置の精度が、シナリオのニーズを基準とする必要があります。たとえば、一般的な表面の配置は、空間のマップを使用できますより正確な配置マーカーおよび調整のいくつかの使用が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-195">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-197"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-198">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-198">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-199">❌</span><span class="sxs-lookup"><span data-stu-id="b41c6-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-200">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-200">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-201">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-201">Best</span></span>  |  <span data-ttu-id="b41c6-202">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-202">Meets</span></span> |  <span data-ttu-id="b41c6-203">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="b41c6-204">ホログラムは、通常は、センチメートルでインチの範囲の画面に揃えます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="b41c6-205">精度が向上する必要がある場合、アプリは、必要なアプリ仕様内のコラボレーションの効率的な方法を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="b41c6-206">該当なし</span><span class="sxs-lookup"><span data-stu-id="b41c6-206">NA</span></span> | <span data-ttu-id="b41c6-207">サーフェスの平面互換性に影響するか、float、画面から離れた場所に表示される、ホログラムが物理的なターゲット オブジェクトにアラインされていない表示されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="b41c6-208">精度が必要な場合、ホログラムはシナリオの近接仕様を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-209">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-209">How to measure</span></span>

* <span data-ttu-id="b41c6-210">ホログラム空間のマップに配置されている必要がありますが大幅に float、画面の上下には表示されません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="b41c6-211">ホログラム正確な配置を必要とするには、何らかの形のマーカーと調整システム シナリオの要件に正確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-212">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-212">Recommendations</span></span>

* <span data-ttu-id="b41c6-213">空間のマップは、有効桁数が必要なサーフェスでオブジェクトを配置するために便利です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="b41c6-214">最適な精度では、マーカーまたはポスターを最終的な調整をホログラムと Xbox コント ローラー (または一部手動の配置メカニズム) を設定するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="b41c6-215">論理部分に非常に大規模なホログラムを分割し、画面には、各部分の配置を検討してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="b41c6-216">不適切なセット interpupilary 距離 (IPD) にホログラム配置も影響することができます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="b41c6-217">常に、ユーザーの IPD に HoloLens を構成します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-218">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-219">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-219">Documentation</span></span>

* [<span data-ttu-id="b41c6-220">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="b41c6-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="b41c6-221">スキャン処理ルーム</span><span class="sxs-lookup"><span data-stu-id="b41c6-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="b41c6-222">空間アンカーのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="b41c6-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="b41c6-223">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="b41c6-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="b41c6-224">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="b41c6-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="b41c6-225">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="b41c6-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-226">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-226">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-227">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="b41c6-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="b41c6-228">MR Toolkit、空間マッピング ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b41c6-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="b41c6-229">MR コンパニオン キット、ポスターの調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="b41c6-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="b41c6-230">MR コンパニオン キット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="b41c6-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="b41c6-231">外部参照</span><span class="sxs-lookup"><span data-stu-id="b41c6-231">External references</span></span>

* [<span data-ttu-id="b41c6-232">Lowes ケース スタディ、有効桁数の配置</span><span class="sxs-lookup"><span data-stu-id="b41c6-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="b41c6-233">快適性のゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="b41c6-233">Viewing zone of comfort</span></span>

<span data-ttu-id="b41c6-234">アプリ開発者のコントロールはコンテンツとホログラムをさまざまな深さで配置することでユーザーの目が収束できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="b41c6-235">HoloLens ソックスを着けずにユーザーは、2.0 m 鮮明な画像は HoloLens に表示されるため、光学距離約 2.0 m ユーザーから離れた場所に固定は維持するために常に可能になります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="b41c6-236">不適切なコンテンツの階層レベルは、visual 不安や疲労につながることができます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-237">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-239"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-240">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-240">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-241">❌</span><span class="sxs-lookup"><span data-stu-id="b41c6-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-242">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="b41c6-243">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="b41c6-244">2 分には、コンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-244">Place content at 2m.</span></span></li><li><span data-ttu-id="b41c6-245">ホログラムは 2 m に配置されることはできず、収束と宿泊施設間の競合を回避することはできません、ホログラムを配置するための最適なゾーンが 1.25 m と 5 分間は。</span><span class="sxs-lookup"><span data-stu-id="b41c6-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="b41c6-246">すべてのケースでは、デザイナーがコンテンツを 1 以上の対話をユーザーに促すことを構成する必要がありますメートル離れた場所 (例: コンテンツのサイズを調整して、既定の配置パラメーター)。</span><span class="sxs-lookup"><span data-stu-id="b41c6-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="b41c6-247">具体的にはないシナリオで必要に応じて、しない限り、クリッピング平面が 1 m で始まる fadeout と実装にあります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="b41c6-248">ようにホログラムの近くの監視が必要な場合は、コンテンツの 50 cm よりも近いしない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="b41c6-249">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-249">Meets</span></span></td><td> <span data-ttu-id="b41c6-250">コンテンツは、内で、表示およびモーションのガイダンスが、不適切な使用またはクリップの平面は使用されていません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b41c6-251">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-251">Fail</span></span> </td><td> <span data-ttu-id="b41c6-252">コンテンツの表示が近すぎる (通常&lt;1.25 m、または&lt;50 cm 静止ホログラムを詳しく監視を必要とするのです)。</span><span class="sxs-lookup"><span data-stu-id="b41c6-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-253">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-253">How to measure</span></span>

* <span data-ttu-id="b41c6-254">コンテンツ通常は 2 m、退席中、1.25 または 5 分よりもさらにより近いいいえ。</span><span class="sxs-lookup"><span data-stu-id="b41c6-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="b41c6-255">いくつかの例外を除き、HoloLens クリッピング レンダリングまでの距離を .85CM に fadeout 1 m からコンテンツを設定してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="b41c6-256">コンテンツのアプローチし、クリッピング平面の影響に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="b41c6-257">静止しているコンテンツを 50 cm 離れたよりも近いすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-258">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-258">Recommendations</span></span>

* <span data-ttu-id="b41c6-259">2 分の最適な表示距離のコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="b41c6-260">コンテンツが 1 m で始まる fadeout と 85 cm クリッピング レンダリングまでの距離を設定します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="b41c6-261">近い場所を表示する必要がある静止ホログラム、30 cm 以内にないはクリップの面で、fadeout は少なくとも 10 cm クリッピング平面からを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-262">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-262">Resources</span></span>

* [<span data-ttu-id="b41c6-263">距離をレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="b41c6-264">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="b41c6-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="b41c6-265">スケールみる</span><span class="sxs-lookup"><span data-stu-id="b41c6-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="b41c6-266">テキスト、フォント サイズの推奨</span><span class="sxs-lookup"><span data-stu-id="b41c6-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="b41c6-267">深さの切り替え</span><span class="sxs-lookup"><span data-stu-id="b41c6-267">Depth switching</span></span>

<span data-ttu-id="b41c6-268">快適性の問題のゾーンを表示に関係なくほぼし、oculomotor の疲労と一般的な不安をする可能性があります (ホログラムと実際のコンテンツを含む) までの焦点のオブジェクト間や頻繁にすばやくを切り替えるユーザーを要求します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-269">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-271"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-272">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-272">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-273">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-274">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-274">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-275">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-275">Best</span></span>  |  <span data-ttu-id="b41c6-276">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-276">Meets</span></span> |  <span data-ttu-id="b41c6-277">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-278">切り替えを限定的または自然の深さが原因で、ユーザーが膨らみます不自然しません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="b41c6-279">これはコアであり、アプリのエクスペリエンスに組み込むの突然の深さスイッチ、または実際の予期しないコンテンツによって発生した突然深さスイッチ。</span><span class="sxs-lookup"><span data-stu-id="b41c6-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="b41c6-280">一貫性のある深さスイッチ、または深さの突然の切り替えは必要のないまたは core アプリのエクスペリエンスをします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-281">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-281">How to measure</span></span>

* <span data-ttu-id="b41c6-282">アプリが一貫してや突然の深さのフォーカスを変更するユーザーが必要な場合は、問題の切り替えの深さです。</span><span class="sxs-lookup"><span data-stu-id="b41c6-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-283">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-283">Recommendations</span></span>

* <span data-ttu-id="b41c6-284">一貫性のある焦点面で主要なコンテンツを保持し、安定化の平面が焦点面と一致するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="b41c6-285">Oculomotor 疲労と予期しないホログラム移動が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-286">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-286">Resources</span></span>

* [<span data-ttu-id="b41c6-287">距離をレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="b41c6-288">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="b41c6-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="b41c6-289">空間のサウンドの使用</span><span class="sxs-lookup"><span data-stu-id="b41c6-289">Use of spatial sound</span></span>

<span data-ttu-id="b41c6-290">Windows Mixed Reality では、オーディオ エンジンは、3 D の方向、距離、および環境のシミュレーションを使用してサウンドをシミュレートすることで、複合現実エクスペリエンスの聴覚的なコンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="b41c6-291">アプリケーションでサウンドの空間を使用すると、ユーザーを囲むが 3 次元空間 (球) でサウンドを配置する開発者ができます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="b41c6-292">それらのサウンドは、実際の物理オブジェクトまたはユーザーの環境での複合現実ホログラムから送信されるがまるでようですが。</span><span class="sxs-lookup"><span data-stu-id="b41c6-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="b41c6-293">サウンドの空間は、immersion、アクセシビリティ、および複合現実のアプリケーションでの UX デザインの強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="b41c6-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-294">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-296"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-297">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-297">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-298">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-299">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-299">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-300">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-300">Best</span></span>  |  <span data-ttu-id="b41c6-301">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-301">Meets</span></span> |  <span data-ttu-id="b41c6-302">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-303">サウンドが spatialized は論理的にし、適切に、UX はオブジェクトの検出とユーザーのフィードバックを支援するサウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="b41c6-304">サウンドがシナリオ全体であり自然なオブジェクトに関連する正規化されました。</span><span class="sxs-lookup"><span data-stu-id="b41c6-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="b41c6-305">空間オーディオは、信憑性で適切に使用されますが、ユーザーからのフィードバックと見つけやすさを支援するための手段として存在します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="b41c6-306">予想どおり、サウンドが spatialized いないや UX 内のユーザーを支援するために、サウンドの欠如</span><span class="sxs-lookup"><span data-stu-id="b41c6-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="b41c6-307">または空間オーディオがないと見なされますまたはシナリオの設計で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-308">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-308">How to measure</span></span>

* <span data-ttu-id="b41c6-309">一般に、関連するサウンドがターゲット ホログラムから出力する必要があります (例:、holographic dog から見かけサウンド。)。</span><span class="sxs-lookup"><span data-stu-id="b41c6-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="b41c6-310">フィードバックや認識 holographic フレーム外のアクションのユーザーを支援するためには、ユーザー エクスペリエンス全体でサウンド キューを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-311">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-311">Recommendations</span></span>

* <span data-ttu-id="b41c6-312">空間オーディオを使用して、オブジェクトの検出とユーザー インターフェイスを支援します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="b41c6-313">サウンドの実際の作業が合成または不自然なサウンドよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="b41c6-314">ほとんどのサウンドを spatialized する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="b41c6-315">発信機を非表示をしないようにします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="b41c6-316">空間のマスクを回避します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="b41c6-317">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-318">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-319">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-319">Documentation</span></span>

* [<span data-ttu-id="b41c6-320">立体音響</span><span class="sxs-lookup"><span data-stu-id="b41c6-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b41c6-321">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="b41c6-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="b41c6-322">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="b41c6-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="b41c6-323">ケース スタディ、HoloTour のサウンドの空間</span><span class="sxs-lookup"><span data-stu-id="b41c6-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="b41c6-324">RoboRaid でサウンドの空間を使用して、ケース スタディ</span><span class="sxs-lookup"><span data-stu-id="b41c6-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-325">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-325">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-326">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="b41c6-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="b41c6-327">MRToolkit、空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="b41c6-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="b41c6-328">Holographic フレーム (FOV) の境界に集中します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="b41c6-329">適切に設計されたユーザー エクスペリエンスを作成し、仮想環境、ユーザーの周りを拡張するのに便利なコンテキストを維持できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="b41c6-330">コンテンツのスケールとコンテキストの親切なデザイン FOV 境界の影響を軽減する必要があります、空間オーディオ、ガイダンスのシステムとユーザーの位置を使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="b41c6-331">場合、ユーザーは快適なアプリ エクスペリエンスをことができますが、FOV 境界によって損なわれる小さいを感じです。</span><span class="sxs-lookup"><span data-stu-id="b41c6-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-332">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-334"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-335">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-335">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-336">❌</span><span class="sxs-lookup"><span data-stu-id="b41c6-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-337">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-337">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-338">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-338">Best</span></span>  |  <span data-ttu-id="b41c6-339">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-339">Meets</span></span> |  <span data-ttu-id="b41c6-340">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-341">ユーザー コンテキストを失うことは、表示する使いやすい。</span><span class="sxs-lookup"><span data-stu-id="b41c6-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="b41c6-342">ラージ オブジェクトのコンテキストのサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="b41c6-343">フレームの外側のオブジェクトの見つけやすさとガイダンスの表示が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="b41c6-344">一般に、モーションの設計と、ホログラムの小数点以下桁数は、快適な表示エクスペリエンスに適しています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="b41c6-345">ユーザーには、コンテキストが失われることが、余分の足部の動きを限られた状況で必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="b41c6-346">限られた状況では、スケールはホログラム ホログラムを表示するには、いくつかネック モーションの原因と垂直方向または水平方向のフレームのいずれかを中断するとします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="b41c6-347">ホログラムを表示するには、ユーザーのコンテキストや首部分の一貫性のあるモーションが失われる可能性がありますが必要です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="b41c6-348">なし、見つけやすさのガイダンスについては、または縦ホログラム フレームの外側に失われやすくオブジェクトの移動、holographic ラージ オブジェクトのコンテキストのガイダンスには、正規の足部の動きを表示する必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-349">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-349">How to measure</span></span>

* <span data-ttu-id="b41c6-350">(大) ホログラムのコンテキストが紛失または境界にクリップされているため認識されません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="b41c6-351">ホログラムの場所は、注意取締役や holographic のフレームとの間にすばやく移動できるコンテンツがないのために見つけにくくします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="b41c6-352">正規表現での足部の疲労ホログラムを完全に表示するヘッド モーションを上下に反復的なシナリオが必要です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-353">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-353">Recommendations</span></span>

* <span data-ttu-id="b41c6-354">視界に合わせて、大きなバージョンを視覚的に移行し、小さなオブジェクトをエクスペリエンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="b41c6-355">空間のオーディオおよび注意ディレクターを使用して、ヘルプ、視界の外にあるユーザーの検索コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="b41c6-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="b41c6-356">垂直方向にクリップの視界ホログラムが、できる限り多くしないでください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="b41c6-357">適切に場所を表示するアプリでのガイダンスをユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-358">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-359">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-359">Documentation</span></span>

* [<span data-ttu-id="b41c6-360">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="b41c6-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="b41c6-361">ケース スタディ、HoloStudio UI および相互作用のデザインの学習</span><span class="sxs-lookup"><span data-stu-id="b41c6-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="b41c6-362">オブジェクトおよび環境のスケール</span><span class="sxs-lookup"><span data-stu-id="b41c6-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="b41c6-363">カーソル、視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="b41c6-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="b41c6-364">外部参照</span><span class="sxs-lookup"><span data-stu-id="b41c6-364">External references</span></span>

* [<span data-ttu-id="b41c6-365">Ado の利用、FOV</span><span class="sxs-lookup"><span data-stu-id="b41c6-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="b41c6-366">コンテンツがユーザーの位置に対応します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-366">Content reacts to user position</span></span>

<span data-ttu-id="b41c6-367">ホログラムは、「実際の」オブジェクトと同じ方法ほぼ内のユーザーの位置に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="b41c6-368">注目すべき設計の考慮事項は、ユーザーの位置を想定できません必ずしも UI 要素が静止していると、ユーザーの動きに合わせては。</span><span class="sxs-lookup"><span data-stu-id="b41c6-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="b41c6-369">ユーザーの位置に正しく対応するアプリをデザインよりかぎりエクスペリエンスの作成し、使いやすきます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-370">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-372"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-373">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-373">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-374">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-375">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="b41c6-376">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-376">Best</span></span> </td><td> <span data-ttu-id="b41c6-377">コンテンツと UI は、自然の想定されるユーザーの移動のスコープ内のコンテンツと対話するユーザーを許可するユーザーの位置に適応します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b41c6-378">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-378">Meets</span></span> </td><td> <span data-ttu-id="b41c6-379">UI は、ユーザーの位置に対応しますが、それらの位置を調整するユーザーを必要とするキーのコンテンツの表示を妨げる可能性が。</span><span class="sxs-lookup"><span data-stu-id="b41c6-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b41c6-380">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="b41c6-381">UI 要素が紛失または、移動の原因となるユーザー コントロールを不自然に戻ります (または見つける) 中にロックされています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="b41c6-382">UI 要素は、主要なコンテンツの表示を制限します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="b41c6-383">特に、運動量との距離を表示するため UI の動きが最適化されていない<a href="billboarding-and-tag-along.md">tag-along</a> UI 要素。</span><span class="sxs-lookup"><span data-stu-id="b41c6-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-384">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-384">How to measure</span></span>

* <span data-ttu-id="b41c6-385">すべての測定値は、シナリオの妥当な範囲内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="b41c6-386">ユーザーの移動はによって異なりますが、極端なユーザーの移動は、アプリをください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="b41c6-387">UI 要素、関連するコントロールをユーザーの移動に関係なく利用してください。</span><span class="sxs-lookup"><span data-stu-id="b41c6-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="b41c6-388">たとえば、ユーザーが表示とズームを使用して 3D マップを歩きながら、ズーム コントロールが場所に関係なく、ユーザーにすぐに使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-389">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-389">Recommendations</span></span>

* <span data-ttu-id="b41c6-390">ユーザーは、カメラであり、動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="b41c6-391">ドライブにできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-391">Let them drive.</span></span>
* <span data-ttu-id="b41c6-392">テキストのためのビルボードを検討してくださいされ帰りシステム world ロックや非表示になる場合、ユーザー、それ以外の場合に移動します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="b41c6-393">前に新機能については、ユーザーを許可する一方、ユーザーをフォローする必要があるコンテンツの tag-along を使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-394">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-395">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-395">Documentation</span></span>

* [<span data-ttu-id="b41c6-396">対話デザイン</span><span class="sxs-lookup"><span data-stu-id="b41c6-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="b41c6-397">色、光、および資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="b41c6-398">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="b41c6-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b41c6-399">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="b41c6-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b41c6-400">自己モーションとユーザー locomotion</span><span class="sxs-lookup"><span data-stu-id="b41c6-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-401">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-401">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-402">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="b41c6-403">入力の相互作用をわかりやすくするため</span><span class="sxs-lookup"><span data-stu-id="b41c6-403">Input interaction clarity</span></span>

<span data-ttu-id="b41c6-404">入力の相互作用をわかりやすくするためは、アプリの有用性に重大な入力の整合性、未成熟、見つけやすさの相互作用の方法が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="b41c6-405">ユーザーは、再確認せずにプラットフォーム全体にわたる一般的な相互作用を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="b41c6-406">アプリにカスタムの入力がある場合が明確に伝達し、説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-407">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-409"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-410">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-410">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-411">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-412">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-412">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-413">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-413">Best</span></span>  |  <span data-ttu-id="b41c6-414">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-414">Meets</span></span> |  <span data-ttu-id="b41c6-415">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-416">入力の対話操作のメソッドは提供されている Windows Mixed Reality で一貫性のある[ガイダンス](interaction-fundamentals.md)します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="b41c6-417">任意のカスタム入力標準入力 (使用して標準的な対話ではなく) と重複することはできません必要があります明確に伝達およびユーザーに示されています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="b41c6-418">同様に最適ですがカスタムの入力は、標準入力方式を冗長です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="b41c6-419">ユーザーの目標とアプリ エクスペリエンスの進行状況を実現できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="b41c6-420">入力メソッドまたはボタンのマッピングを理解するのには困難です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="b41c6-421">入力が大きくカスタマイズされて、なしの手順については、標準の入力をサポートしていませんまたは疲労と快適性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-422">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-422">How to measure</span></span>

* <span data-ttu-id="b41c6-423">アプリで使用する一貫性のある[標準入力方式。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="b41c6-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="b41c6-424">アプリにカスタムの入力がある場合は、それを明確にを通じてを伝達します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="b41c6-425">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="b41c6-425">First-run experience</span></span>
* <span data-ttu-id="b41c6-426">概要画面</span><span class="sxs-lookup"><span data-stu-id="b41c6-426">Introductory screens</span></span>
* <span data-ttu-id="b41c6-427">ヒント</span><span class="sxs-lookup"><span data-stu-id="b41c6-427">Tooltips</span></span>
* <span data-ttu-id="b41c6-428">手動指導者</span><span class="sxs-lookup"><span data-stu-id="b41c6-428">Hand coach</span></span>
* <span data-ttu-id="b41c6-429">ヘルプ セクション</span><span class="sxs-lookup"><span data-stu-id="b41c6-429">Help section</span></span>
* <span data-ttu-id="b41c6-430">ボイス オーバー</span><span class="sxs-lookup"><span data-stu-id="b41c6-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-431">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-431">Recommendations</span></span>

* <span data-ttu-id="b41c6-432">可能な限り標準の入力メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="b41c6-433">標準以外の入力方法のデモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="b41c6-434">アプリ全体で一貫性のある相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-435">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-436">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-436">Documentation</span></span>

* [<span data-ttu-id="b41c6-437">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="b41c6-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b41c6-438">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b41c6-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="b41c6-439">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="b41c6-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b41c6-440">カーソル</span><span class="sxs-lookup"><span data-stu-id="b41c6-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b41c6-441">快適性と視線入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="b41c6-442">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="b41c6-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b41c6-443">音声入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b41c6-444">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="b41c6-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="b41c6-445">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="b41c6-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="b41c6-446">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="b41c6-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="b41c6-447">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="b41c6-448">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="b41c6-449">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="b41c6-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="b41c6-450">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="b41c6-451">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="b41c6-452">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="b41c6-453">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="b41c6-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="b41c6-454">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-455">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-455">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-456">ケース スタディ:複数のパーソナル コンピューティングのフォロー アップ</span><span class="sxs-lookup"><span data-stu-id="b41c6-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="b41c6-457">調査をキャストします。HoloStudio UI との対話デザインの学習内容</span><span class="sxs-lookup"><span data-stu-id="b41c6-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="b41c6-458">サンプル アプリ:要素の定期処理テーブル</span><span class="sxs-lookup"><span data-stu-id="b41c6-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="b41c6-459">サンプル アプリ:旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="b41c6-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="b41c6-460">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="b41c6-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="b41c6-461">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="b41c6-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="b41c6-462">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="b41c6-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="b41c6-463">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b41c6-463">Interactable objects</span></span>

<span data-ttu-id="b41c6-464">ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="b41c6-465">3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="b41c6-466">イベントをトリガーする対話型のオブジェクトを何も指定できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="b41c6-467">対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="b41c6-468">形式に関係なく対話型のオブジェクトを視覚的およびオーディオをユーザーが明確に認識できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-469">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-471"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-472">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-472">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-473">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-474">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-474">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-475">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-475">Best</span></span>  |  <span data-ttu-id="b41c6-476">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-476">Meets</span></span> |  <span data-ttu-id="b41c6-477">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-478">3 つの状態の間で視覚的およびオーディオを認識できるものは対話型のオブジェクト、形式に関係なく: アイドル状態をターゲットとして、選択します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="b41c6-479">「に言ってを参照してください」がオフで、一貫した使用エクスペリエンスのあらゆる場所。</span><span class="sxs-lookup"><span data-stu-id="b41c6-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="b41c6-480">オブジェクトは拡大縮小され、エラーを対象とする無料のために分散します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="b41c6-481">ユーザーできますオーディオまたはビデオのフィードバックを通じた対話型としてオブジェクトを認識およびできますターゲットし、オブジェクトをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="b41c6-482">ビジュアルやオーディオ キューを指定しない場合は、ユーザーは対話型のオブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="b41c6-483">相互作用は、間違いやすくオブジェクト スケールまたはオブジェクト間の距離が原因です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-484">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-484">How to measure</span></span>

* <span data-ttu-id="b41c6-485">対話型のオブジェクトが '対話型'; として認識できます。特定のボタン、メニューのおよびアプリのコンテンツを含むです。</span><span class="sxs-lookup"><span data-stu-id="b41c6-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="b41c6-486">経験則として必要がありますビジュアルおよびオーディオ キュー対話型のオブジェクトを対象とする場合。</span><span class="sxs-lookup"><span data-stu-id="b41c6-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-487">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-487">Recommendations</span></span>

* <span data-ttu-id="b41c6-488">相互作用のビジュアルおよびオーディオのフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="b41c6-489">それぞれの入力 (アイドル状態、対象となる、選択した) の状態の視覚的なフィードバックを区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="b41c6-490">対話型のオブジェクトを拡張し、エラーを対象とする無料の配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="b41c6-491">(メニュー バーやリスト) グループ化された対話型のオブジェクトには、適切な間隔を対象とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="b41c6-492">音声コマンドをサポートするボタンとメニューは、キーワードのコマンドのテキスト ラベルを指定する必要があります (「表示, に言って」)</span><span class="sxs-lookup"><span data-stu-id="b41c6-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-493">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-494">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-494">Documentation</span></span>

* [<span data-ttu-id="b41c6-495">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b41c6-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b41c6-496">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="b41c6-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b41c6-497">アプリ バーと境界ボックス</span><span class="sxs-lookup"><span data-stu-id="b41c6-497">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b41c6-498">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="b41c6-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-499">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-499">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-500">Mixed Reality Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="b41c6-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="b41c6-501">ルームのスキャン</span><span class="sxs-lookup"><span data-stu-id="b41c6-501">Room scanning</span></span>

<span data-ttu-id="b41c6-502">空間マッピング データを必要とするアプリでは、時間の経過と共に自動的にこのデータを収集するデバイスに依存しており、ユーザーとセッション間でアクティブなデバイスでの環境について説明します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="b41c6-503">完全を期すため、このデータの品質は、さまざまなユーザーが行った探索の量、探索からどれ時間だけが経過や、デバイス、領域をスキャンするので家具や扉などのオブジェクトが移動するかどうかなどの要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="b41c6-504">多くのアプリでは、ユーザーが、完全を期すためと、空間のマップの品質を向上させるために追加の手順を実行する必要があるかどうかを判断するエクスペリエンスの先頭に空間マッピング データを分析します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="b41c6-505">場合は、ユーザーが、スキャン時にガイダンスが提供される必要があります明確、環境をスキャンするために必要です。</span><span class="sxs-lookup"><span data-stu-id="b41c6-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-506">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-508"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-509">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-509">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-510">❌</span><span class="sxs-lookup"><span data-stu-id="b41c6-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-511">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-511">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-512">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-512">Best</span></span>  |  <span data-ttu-id="b41c6-513">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-513">Meets</span></span> |  <span data-ttu-id="b41c6-514">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-515">空間メッシュの視覚化は、ユーザーのスキャンが進行中に伝えます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="b41c6-516">ユーザーは、対処方法と、スキャンが開始し、停止に明確に認識しています。</span><span class="sxs-lookup"><span data-stu-id="b41c6-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="b41c6-517">空間のメッシュの視覚エフェクトが提供されますが、ユーザーが明確に対処できないを行うと進行状況に関する情報は提供されません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="b41c6-518">メッシュの視覚表現はありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-518">No visualization of mesh.</span></span> <span data-ttu-id="b41c6-519">ガイダンスの情報を探すには、where 句またはときに、スキャンを開始または停止についてユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-520">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-520">How to measure</span></span>

* <span data-ttu-id="b41c6-521">必要なルーム スキャン中に、検索する場所を開始して停止のスキャンを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-522">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-522">Recommendations</span></span>

* <span data-ttu-id="b41c6-523">エクスペリエンスの一部である必要があるユーザーの近くの合計ボリュームの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="b41c6-524">スキャンが開始され、進行状況インジケーターなどを停止すると通信します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="b41c6-525">スキャン中に、メッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="b41c6-526">検索し、ルーム内を移動するユーザーを促すビジュアルおよびオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="b41c6-527">データを向上させるために移動する場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="b41c6-528">多くの場合に必要な内容の操作を行います (例: を見て、ceiling 見て家具の背後にある)、ユーザーに伝えるための最適な場合があります、スキャンのために必要な品質を取得するためにします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-529">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b41c6-530">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="b41c6-530">Documentation</span></span>

* [<span data-ttu-id="b41c6-531">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="b41c6-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="b41c6-532">ケース スタディ:HoloLens の空間のマッピング機能を展開します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="b41c6-533">ケース スタディ:空間 HoloTour の設計</span><span class="sxs-lookup"><span data-stu-id="b41c6-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="b41c6-534">ケース スタディ:フラグメントで魅力的なエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b41c6-535">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="b41c6-535">Tools and tutorials</span></span>

* [<span data-ttu-id="b41c6-536">Mixed Reality Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="b41c6-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="b41c6-537">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="b41c6-537">Directional indicators</span></span>

<span data-ttu-id="b41c6-538">Mixed reality アプリでは、コンテンツは、ビューのフィールドの外側にありますか、現実世界のオブジェクトによってオクルー ジョンします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="b41c6-539">適切に設計されたアプリは簡単に表示されているコンテンツを検索するユーザー。</span><span class="sxs-lookup"><span data-stu-id="b41c6-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="b41c6-540">方向インジケーターは、重要なコンテンツをユーザーに警告し、ユーザーの位置を基準としたコンテンツへのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="b41c6-541">非表示のコンテンツへのガイダンスには、サウンドのエミッタ、方向矢印、または直接の視覚的な手掛かりのフォームを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-542">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-544"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-545">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-545">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-546">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-547">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-547">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-548">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-548">Best</span></span>  |  <span data-ttu-id="b41c6-549">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-549">Meets</span></span> |  <span data-ttu-id="b41c6-550">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-551">ビジュアルおよびオーディオ キューは、ビューのフィールドの外側の関連するコンテンツに直接ユーザーを説明します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="b41c6-552">矢印またはコンテンツの全体的な方向性で、ユーザーを示すいくつかのインジケーター。</span><span class="sxs-lookup"><span data-stu-id="b41c6-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="b41c6-553">関連するコンテンツが視野、外部と低いか、ユーザーに場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-554">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-554">How to measure</span></span>

* <span data-ttu-id="b41c6-555">ビューのユーザー フィールドの外部で関連するコンテンツでは、ビジュアルおよびオーディオ キューを検出します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-556">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-556">Recommendations</span></span>

* <span data-ttu-id="b41c6-557">関連するコンテンツは、外部のユーザーのフィールドの表示が、コンテンツにユーザーをガイドするのに方向インジケーターとオーディオ キューを使用します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="b41c6-558">多くの場合、直接 visual ガイドことをお勧め方向矢印にします。</span><span class="sxs-lookup"><span data-stu-id="b41c6-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="b41c6-559">方向インジケーターは、カーソルに組み込まないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-560">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-560">Resources</span></span>

* [<span data-ttu-id="b41c6-561">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="b41c6-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="b41c6-562">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="b41c6-562">Data loading</span></span>

<span data-ttu-id="b41c6-563">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="b41c6-564">ユーザーは、進行状況インジケーターが表示されると、待機時間はどれくらいの時間ありますを示すことも、アプリで操作できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b41c6-565">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="b41c6-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b41c6-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b41c6-567"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b41c6-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b41c6-568">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-568">✔️</span></span></td>
        <td><span data-ttu-id="b41c6-569">✔️</span><span class="sxs-lookup"><span data-stu-id="b41c6-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b41c6-570">品質基準</span><span class="sxs-lookup"><span data-stu-id="b41c6-570">Quality criteria</span></span>

|  <span data-ttu-id="b41c6-571">最高</span><span class="sxs-lookup"><span data-stu-id="b41c6-571">Best</span></span>  |  <span data-ttu-id="b41c6-572">満たす</span><span class="sxs-lookup"><span data-stu-id="b41c6-572">Meets</span></span> |  <span data-ttu-id="b41c6-573">失敗</span><span class="sxs-lookup"><span data-stu-id="b41c6-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b41c6-574">進行状況バーや任意のデータの読み込みまたは処理中に進行状況を示すリングの形式で、視覚的なインジケーターをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="b41c6-575">視覚インジケータは、どのくらいの時間待機する可能性がありますにガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="b41c6-576">データの読み込みが進行中ではどのくらいの時間、待機できることを示す値はありませんが、ユーザーが通知されます。</span><span class="sxs-lookup"><span data-stu-id="b41c6-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="b41c6-577">データの読み込みまたはプロセスのインジケーターを 5 秒以上かかったタスクがありません。</span><span class="sxs-lookup"><span data-stu-id="b41c6-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b41c6-578">測定する方法</span><span class="sxs-lookup"><span data-stu-id="b41c6-578">How to measure</span></span>

* <span data-ttu-id="b41c6-579">データの読み込み中には、5 秒以上の空の状態はありませんを確認します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b41c6-580">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b41c6-580">Recommendations</span></span>

* <span data-ttu-id="b41c6-581">ユーザーがこのアプリが停止しているか、クラッシュするを感じる可能性がある場合に、どのような状況で進行状況を示すデータ読み込み animator を提供します。</span><span class="sxs-lookup"><span data-stu-id="b41c6-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="b41c6-582">妥当な経験則は、'ロード' アクティビティで 5 秒以上かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b41c6-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="b41c6-583">参考資料</span><span class="sxs-lookup"><span data-stu-id="b41c6-583">Resources</span></span>

* [<span data-ttu-id="b41c6-584">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="b41c6-584">Displaying progress</span></span>](progress.md)
