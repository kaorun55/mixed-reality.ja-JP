---
title: アプリの品質基準
description: このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリの品質基準、実際には、混合 mixed reality アプリ
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024496"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="9d68d-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-104">App quality criteria</span></span>

<span data-ttu-id="9d68d-105">このドキュメントでは、複合現実アプリの品質に影響を与える主な理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="9d68d-106">次の情報を提供する各要素について</span><span class="sxs-lookup"><span data-stu-id="9d68d-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="9d68d-107">概要 – の品質要因と重要な理由の簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="9d68d-108">デバイスによる影響 - Mixed Reality をウィンドウのデバイスの種類は影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="9d68d-109">品質基準 – の品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="9d68d-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="9d68d-110">– メソッドに、問題を計測 (またはエクスペリエンス) を測定する方法。</span><span class="sxs-lookup"><span data-stu-id="9d68d-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="9d68d-111">推奨事項のより優れたユーザー エクスペリエンスを提供する方法の概要。</span><span class="sxs-lookup"><span data-stu-id="9d68d-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="9d68d-112">リソース-関連する開発者とアプリのより優れたエクスペリエンスを作成すると便利であるデザイン リソース</span><span class="sxs-lookup"><span data-stu-id="9d68d-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="9d68d-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="9d68d-113">Frame rate</span></span>

<span data-ttu-id="9d68d-114">フレーム レートはホログラムの安定性とユーザーの快適性の最初の柱です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="9d68d-115">推奨されるターゲットの下のフレーム レートには、ホログラムちらついたり、エクスペリエンスの信憑性に悪影響を与えると、目の疲労が発生する可能性を表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="9d68d-116">Windows Mixed Reality イマーシブ ヘッドセットでのユーザー エクスペリエンスのターゲット フレーム レートは、60 Hz またはサポートする Windows Mixed Reality 互換性のある Pc に応じて 90 Hz のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="9d68d-117">HoloLens 先のフレーム レートは 60 Hz です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-121">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-121">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-122">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-123">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-124">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-124">Best</span></span>  |  <span data-ttu-id="9d68d-125">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-125">Meets</span></span> |  <span data-ttu-id="9d68d-126">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9d68d-127">アプリでは、一貫してターゲット デバイスの 2 つ目の (FPS) 目標あたりのフレーム数を満たしています。HoloLens; に 60 fps90 超 Pc; fpsメイン ストリームの Pc で 60 fps します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="9d68d-128">アプリは、コア エクスペリエンスを妨げていない断続的なフレームのドロップまたは、FPS は一貫して目標より低いが、アプリのエクスペリエンスを妨げるありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="9d68d-129">アプリには、フレーム レートの平均が 10 秒ごとに以下のドロップが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9d68d-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-130">How to measure</span></span>

* <span data-ttu-id="9d68d-131">リアルタイムのフレーム レートのグラフがを通じてによって提供される、 [Windows Device Portal](using-the-windows-device-portal.md#system-performance) 「システムのパフォーマンス」の下。</span><span class="sxs-lookup"><span data-stu-id="9d68d-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="9d68d-132">開発のデバッグには、アプリにフレーム レートの診断カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="9d68d-133">サンプルのカウンターは、リソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="9d68d-134">フレーム レートの低下は、頭を左右に移動することによって、アプリの実行中に、デバイスで発生することができます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="9d68d-135">ホログラムちらつく移動の予期しない場合は、フレーム レートが低い、または安定性の面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-136">Recommendations</span></span>

* <span data-ttu-id="9d68d-137">開発作業の開始時に、フレーム レート カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9d68d-138">フレーム レートの低下が発生する変更を評価して、パフォーマンス バグとして適切に解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-139">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-140">Documentation</span></span>

* [<span data-ttu-id="9d68d-141">複合現実のパフォーマンスを理解</span><span class="sxs-lookup"><span data-stu-id="9d68d-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9d68d-142">ホログラム安定性とフレーム レート</span><span class="sxs-lookup"><span data-stu-id="9d68d-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9d68d-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="9d68d-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="9d68d-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-145">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-146">MRToolkit、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="9d68d-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="9d68d-147">MRToolkit、シェーダー</span><span class="sxs-lookup"><span data-stu-id="9d68d-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="9d68d-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="9d68d-148">External references</span></span>

* [<span data-ttu-id="9d68d-149">Unity では、モバイル アプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="9d68d-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="9d68d-150">ホログラム安定性</span><span class="sxs-lookup"><span data-stu-id="9d68d-150">Hologram stability</span></span>

<span data-ttu-id="9d68d-151">安定したホログラムは、使いやすさと、アプリの信憑性を向上し、ユーザーの使いやすい表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="9d68d-152">ホログラム安定性の品質が適切なアプリの開発と (追跡) を理解するデバイスの機能の結果をその環境。</span><span class="sxs-lookup"><span data-stu-id="9d68d-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="9d68d-153">フレーム レートが安定性の最初の柱の中、その他の要因の安定性を含む影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="9d68d-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="9d68d-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="9d68d-155">空間アンカーまでの距離</span><span class="sxs-lookup"><span data-stu-id="9d68d-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="9d68d-156">Tracking</span><span class="sxs-lookup"><span data-stu-id="9d68d-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-159"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-160">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-160">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-161">❌</span><span class="sxs-lookup"><span data-stu-id="9d68d-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-162">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-162">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-163">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-163">Best</span></span>  |  <span data-ttu-id="9d68d-164">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-164">Meets</span></span> |  <span data-ttu-id="9d68d-165">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-166">ホログラムが一貫して安定したが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="9d68d-167">セカンダリのコンテンツは予期しない動きです。または、予期しない動きが全体的なアプリ エクスペリエンスを妨げるありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="9d68d-168">フレームで主要なコンテンツには、予期せぬ動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-169">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-169">How to measure</span></span>

<span data-ttu-id="9d68d-170">While ソックスを着けずに、デバイスと、エクスペリエンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="9d68d-171">サイド バイ サイドに頭を移動、ホログラムが予期しない動きを表示する場合、フレーム レートが低いまたは焦点面に安定性の面の不適切なアラインメントは考えられる原因になります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="9d68d-172">ホログラムや環境を移動、スイムレーンと jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="9d68d-173">この種類のアニメーションは、空間アンカーに環境、または距離を追跡しないデバイスによる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="9d68d-174">大規模な場合、または複数ホログラムがフレームでは、安定化平面に起因揺れの可能性がありますが表示された場合、並列で、ヘッドの位置を移動中に、さまざまな深さでホログラム動作を観察します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="9d68d-175">Recomendations</span><span class="sxs-lookup"><span data-stu-id="9d68d-175">Recomendations</span></span>

* <span data-ttu-id="9d68d-176">開発作業の開始時、フレーム レート カウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9d68d-177">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="9d68d-178">常に、アンカーの 3 つのメートル単位でアンカー ホログラムをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="9d68d-179">環境の適切な追跡のためのセットアップを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="9d68d-180">フレーム内でさまざまな焦点の深さのレベルでホログラムを回避するために、エクスペリエンスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-181">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-182">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-182">Documentation</span></span>

* [<span data-ttu-id="9d68d-183">ホログラム安定性とフレーム レート</span><span class="sxs-lookup"><span data-stu-id="9d68d-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9d68d-184">安定化平面を使用して、ケース スタディ</span><span class="sxs-lookup"><span data-stu-id="9d68d-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="9d68d-185">複合現実のパフォーマンスを理解</span><span class="sxs-lookup"><span data-stu-id="9d68d-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9d68d-186">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="9d68d-187">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="9d68d-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="9d68d-188">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="9d68d-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9d68d-189">フレームの静止した基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-190">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-190">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-191">MR コンパニオン キット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9d68d-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="9d68d-192">実際の画面上の位置をホログラム</span><span class="sxs-lookup"><span data-stu-id="9d68d-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="9d68d-193">物理オブジェクト相互の関連配置するためのもの) であればホログラムのずれは、ホログラムと実際の非結合の明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="9d68d-194">配置の精度が、シナリオのニーズを基準とする必要があります。たとえば、一般的な表面の配置は、空間のマップを使用できますより正確な配置マーカーおよび調整のいくつかの使用が必要になります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-195">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-197"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-198">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-198">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-199">❌</span><span class="sxs-lookup"><span data-stu-id="9d68d-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-200">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-200">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-201">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-201">Best</span></span>  |  <span data-ttu-id="9d68d-202">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-202">Meets</span></span> |  <span data-ttu-id="9d68d-203">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9d68d-204">ホログラムは、通常は、センチメートルでインチの範囲の画面に揃えます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="9d68d-205">精度が向上する必要がある場合、アプリは、必要なアプリ仕様内のコラボレーションの効率的な方法を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="9d68d-206">該当なし</span><span class="sxs-lookup"><span data-stu-id="9d68d-206">NA</span></span> | <span data-ttu-id="9d68d-207">サーフェスの平面互換性に影響するか、float、画面から離れた場所に表示される、ホログラムが物理的なターゲット オブジェクトにアラインされていない表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="9d68d-208">精度が必要な場合、ホログラムはシナリオの近接仕様を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-209">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-209">How to measure</span></span>

* <span data-ttu-id="9d68d-210">ホログラム空間のマップに配置されている必要がありますが大幅に float、画面の上下には表示されません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="9d68d-211">ホログラム正確な配置を必要とするには、何らかの形のマーカーと調整システム シナリオの要件に正確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-212">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-212">Recommendations</span></span>

* <span data-ttu-id="9d68d-213">空間のマップは、有効桁数が必要なサーフェスでオブジェクトを配置するために便利です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="9d68d-214">最適な精度では、マーカーまたはポスターを最終的な調整をホログラムと Xbox コント ローラー (または一部手動の配置メカニズム) を設定するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="9d68d-215">論理部分に非常に大規模なホログラムを分割し、画面には、各部分の配置を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="9d68d-216">不適切なセット interpupilary 距離 (IPD) にホログラム配置も影響することができます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="9d68d-217">常に、ユーザーの IPD に HoloLens を構成します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-218">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-219">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-219">Documentation</span></span>

* [<span data-ttu-id="9d68d-220">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="9d68d-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="9d68d-221">スキャン処理ルーム</span><span class="sxs-lookup"><span data-stu-id="9d68d-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9d68d-222">空間アンカーのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="9d68d-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="9d68d-223">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="9d68d-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9d68d-224">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="9d68d-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="9d68d-225">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="9d68d-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-226">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-226">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-227">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="9d68d-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="9d68d-228">MR Toolkit、空間マッピング ライブラリ</span><span class="sxs-lookup"><span data-stu-id="9d68d-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="9d68d-229">MR コンパニオン キット、ポスターの調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="9d68d-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="9d68d-230">MR コンパニオン キット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9d68d-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="9d68d-231">外部参照</span><span class="sxs-lookup"><span data-stu-id="9d68d-231">External references</span></span>

* [<span data-ttu-id="9d68d-232">Lowes ケース スタディ、有効桁数の配置</span><span class="sxs-lookup"><span data-stu-id="9d68d-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="9d68d-233">快適性のゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="9d68d-233">Viewing zone of comfort</span></span>

<span data-ttu-id="9d68d-234">アプリ開発者のコントロールはコンテンツとホログラムをさまざまな深さで配置することでユーザーの目が収束できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="9d68d-235">HoloLens ソックスを着けずにユーザーは、2.0 m 鮮明な画像は HoloLens に表示されるため、光学距離約 2.0 m ユーザーから離れた場所に固定は維持するために常に可能になります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="9d68d-236">不適切なコンテンツの階層レベルは、visual 不安や疲労につながることができます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-237">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-239"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-240">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-240">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-241">❌</span><span class="sxs-lookup"><span data-stu-id="9d68d-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-242">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9d68d-243">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="9d68d-244">2 分には、コンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-244">Place content at 2m.</span></span></li><li><span data-ttu-id="9d68d-245">ホログラムは 2 m に配置されることはできず、収束と宿泊施設間の競合を回避することはできません、ホログラムを配置するための最適なゾーンが 1.25 m と 5 分間は。</span><span class="sxs-lookup"><span data-stu-id="9d68d-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="9d68d-246">すべてのケースでは、デザイナーがコンテンツを 1 以上の対話をユーザーに促すことを構成する必要がありますメートル離れた場所 (例: コンテンツのサイズを調整して、既定の配置パラメーター)。</span><span class="sxs-lookup"><span data-stu-id="9d68d-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="9d68d-247">具体的にはないシナリオで必要に応じて、しない限り、クリッピング平面が 1 m で始まる fadeout と実装にあります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="9d68d-248">ようにホログラムの近くの監視が必要な場合は、コンテンツの 50 cm よりも近いしない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="9d68d-249">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-249">Meets</span></span></td><td> <span data-ttu-id="9d68d-250">コンテンツは、内で、表示およびモーションのガイダンスが、不適切な使用またはクリップの平面は使用されていません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9d68d-251">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-251">Fail</span></span> </td><td> <span data-ttu-id="9d68d-252">コンテンツの表示が近すぎる (通常&lt;1.25 m、または&lt;50 cm 静止ホログラムを詳しく監視を必要とするのです)。</span><span class="sxs-lookup"><span data-stu-id="9d68d-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-253">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-253">How to measure</span></span>

* <span data-ttu-id="9d68d-254">コンテンツ通常は 2 m、退席中、1.25 または 5 分よりもさらにより近いいいえ。</span><span class="sxs-lookup"><span data-stu-id="9d68d-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="9d68d-255">いくつかの例外を除き、HoloLens クリッピング レンダリングまでの距離を .85CM に fadeout 1 m からコンテンツを設定してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="9d68d-256">コンテンツのアプローチし、クリッピング平面の影響に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="9d68d-257">静止しているコンテンツを 50 cm 離れたよりも近いすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-258">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-258">Recommendations</span></span>

* <span data-ttu-id="9d68d-259">2 分の最適な表示距離のコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="9d68d-260">コンテンツが 1 m で始まる fadeout と 85 cm クリッピング レンダリングまでの距離を設定します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="9d68d-261">近い場所を表示する必要がある静止ホログラム、30 cm 以内にないはクリップの面で、fadeout は少なくとも 10 cm クリッピング平面からを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-262">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-262">Resources</span></span>

* [<span data-ttu-id="9d68d-263">距離をレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9d68d-264">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="9d68d-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="9d68d-265">スケールみる</span><span class="sxs-lookup"><span data-stu-id="9d68d-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="9d68d-266">テキスト、フォント サイズの推奨</span><span class="sxs-lookup"><span data-stu-id="9d68d-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="9d68d-267">深さの切り替え</span><span class="sxs-lookup"><span data-stu-id="9d68d-267">Depth switching</span></span>

<span data-ttu-id="9d68d-268">快適性の問題のゾーンを表示に関係なくほぼし、oculomotor の疲労と一般的な不安をする可能性があります (ホログラムと実際のコンテンツを含む) までの焦点のオブジェクト間や頻繁にすばやくを切り替えるユーザーを要求します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-269">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-271"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-272">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-272">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-273">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-274">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-274">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-275">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-275">Best</span></span>  |  <span data-ttu-id="9d68d-276">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-276">Meets</span></span> |  <span data-ttu-id="9d68d-277">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-278">切り替えを限定的または自然の深さが原因で、ユーザーが膨らみます不自然しません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="9d68d-279">これはコアであり、アプリのエクスペリエンスに組み込むの突然の深さスイッチ、または実際の予期しないコンテンツによって発生した突然深さスイッチ。</span><span class="sxs-lookup"><span data-stu-id="9d68d-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="9d68d-280">一貫性のある深さスイッチ、または深さの突然の切り替えは必要のないまたは core アプリのエクスペリエンスをします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-281">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-281">How to measure</span></span>

* <span data-ttu-id="9d68d-282">アプリが一貫してや突然の深さのフォーカスを変更するユーザーが必要な場合は、問題の切り替えの深さです。</span><span class="sxs-lookup"><span data-stu-id="9d68d-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-283">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-283">Recommendations</span></span>

* <span data-ttu-id="9d68d-284">一貫性のある焦点面で主要なコンテンツを保持し、安定化の平面が焦点面と一致するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="9d68d-285">Oculomotor 疲労と予期しないホログラム移動が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-286">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-286">Resources</span></span>

* [<span data-ttu-id="9d68d-287">距離をレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9d68d-288">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="9d68d-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="9d68d-289">空間のサウンドの使用</span><span class="sxs-lookup"><span data-stu-id="9d68d-289">Use of spatial sound</span></span>

<span data-ttu-id="9d68d-290">Windows Mixed Reality では、オーディオ エンジンは、3 D の方向、距離、および環境のシミュレーションを使用してサウンドをシミュレートすることで、複合現実エクスペリエンスの聴覚的なコンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="9d68d-291">アプリケーションでサウンドの空間を使用すると、ユーザーを囲むが 3 次元空間 (球) でサウンドを配置する開発者ができます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="9d68d-292">それらのサウンドは、実際の物理オブジェクトまたはユーザーの環境での複合現実ホログラムから送信されるがまるでようですが。</span><span class="sxs-lookup"><span data-stu-id="9d68d-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="9d68d-293">サウンドの空間は、immersion、アクセシビリティ、および複合現実のアプリケーションでの UX デザインの強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="9d68d-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-294">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-296"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-297">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-297">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-298">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-299">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-299">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-300">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-300">Best</span></span>  |  <span data-ttu-id="9d68d-301">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-301">Meets</span></span> |  <span data-ttu-id="9d68d-302">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-303">サウンドが spatialized は論理的にし、適切に、UX はオブジェクトの検出とユーザーのフィードバックを支援するサウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="9d68d-304">サウンドがシナリオ全体であり自然なオブジェクトに関連する正規化されました。</span><span class="sxs-lookup"><span data-stu-id="9d68d-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="9d68d-305">空間オーディオは、信憑性で適切に使用されますが、ユーザーからのフィードバックと見つけやすさを支援するための手段として存在します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="9d68d-306">予想どおり、サウンドが spatialized いないや UX 内のユーザーを支援するために、サウンドの欠如</span><span class="sxs-lookup"><span data-stu-id="9d68d-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="9d68d-307">または空間オーディオがないと見なされますまたはシナリオの設計で使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-308">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-308">How to measure</span></span>

* <span data-ttu-id="9d68d-309">一般に、関連するサウンドがターゲット ホログラムから出力する必要があります (例:、holographic dog から見かけサウンド。)。</span><span class="sxs-lookup"><span data-stu-id="9d68d-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="9d68d-310">フィードバックや認識 holographic フレーム外のアクションのユーザーを支援するためには、ユーザー エクスペリエンス全体でサウンド キューを使用してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-311">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-311">Recommendations</span></span>

* <span data-ttu-id="9d68d-312">空間オーディオを使用して、オブジェクトの検出とユーザー インターフェイスを支援します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="9d68d-313">サウンドの実際の作業が合成または不自然なサウンドよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="9d68d-314">ほとんどのサウンドを spatialized する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="9d68d-315">発信機を非表示をしないようにします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="9d68d-316">空間のマスクを回避します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="9d68d-317">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-318">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-319">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-319">Documentation</span></span>

* [<span data-ttu-id="9d68d-320">立体音響</span><span class="sxs-lookup"><span data-stu-id="9d68d-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="9d68d-321">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="9d68d-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="9d68d-322">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="9d68d-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="9d68d-323">ケース スタディ、HoloTour のサウンドの空間</span><span class="sxs-lookup"><span data-stu-id="9d68d-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9d68d-324">RoboRaid でサウンドの空間を使用して、ケース スタディ</span><span class="sxs-lookup"><span data-stu-id="9d68d-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-325">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-325">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-326">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="9d68d-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="9d68d-327">MRToolkit、空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="9d68d-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="9d68d-328">Holographic フレーム (FOV) の境界に集中します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="9d68d-329">適切に設計されたユーザー エクスペリエンスを作成し、仮想環境、ユーザーの周りを拡張するのに便利なコンテキストを維持できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="9d68d-330">コンテンツのスケールとコンテキストの親切なデザイン FOV 境界の影響を軽減する必要があります、空間オーディオ、ガイダンスのシステムとユーザーの位置を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="9d68d-331">場合、ユーザーは快適なアプリ エクスペリエンスをことができますが、FOV 境界によって損なわれる小さいを感じです。</span><span class="sxs-lookup"><span data-stu-id="9d68d-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-332">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-334"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-335">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-335">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-336">❌</span><span class="sxs-lookup"><span data-stu-id="9d68d-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-337">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-337">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-338">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-338">Best</span></span>  |  <span data-ttu-id="9d68d-339">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-339">Meets</span></span> |  <span data-ttu-id="9d68d-340">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-341">ユーザー コンテキストを失うことは、表示する使いやすい。</span><span class="sxs-lookup"><span data-stu-id="9d68d-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="9d68d-342">ラージ オブジェクトのコンテキストのサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="9d68d-343">フレームの外側のオブジェクトの見つけやすさとガイダンスの表示が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="9d68d-344">一般に、モーションの設計と、ホログラムの小数点以下桁数は、快適な表示エクスペリエンスに適しています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="9d68d-345">ユーザーには、コンテキストが失われることが、余分の足部の動きを限られた状況で必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="9d68d-346">限られた状況では、スケールはホログラム ホログラムを表示するには、いくつかネック モーションの原因と垂直方向または水平方向のフレームのいずれかを中断するとします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="9d68d-347">ホログラムを表示するには、ユーザーのコンテキストや首部分の一貫性のあるモーションが失われる可能性がありますが必要です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="9d68d-348">なし、見つけやすさのガイダンスについては、または縦ホログラム フレームの外側に失われやすくオブジェクトの移動、holographic ラージ オブジェクトのコンテキストのガイダンスには、正規の足部の動きを表示する必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-349">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-349">How to measure</span></span>

* <span data-ttu-id="9d68d-350">(大) ホログラムのコンテキストが紛失または境界にクリップされているため認識されません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="9d68d-351">ホログラムの場所は、注意取締役や holographic のフレームとの間にすばやく移動できるコンテンツがないのために見つけにくくします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="9d68d-352">正規表現での足部の疲労ホログラムを完全に表示するヘッド モーションを上下に反復的なシナリオが必要です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-353">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-353">Recommendations</span></span>

* <span data-ttu-id="9d68d-354">視界に合わせて、大きなバージョンを視覚的に移行し、小さなオブジェクトをエクスペリエンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="9d68d-355">空間のオーディオおよび注意ディレクターを使用して、ヘルプ、視界の外にあるユーザーの検索コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="9d68d-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="9d68d-356">垂直方向にクリップの視界ホログラムが、できる限り多くしないでください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="9d68d-357">適切に場所を表示するアプリでのガイダンスをユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-358">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-359">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-359">Documentation</span></span>

* [<span data-ttu-id="9d68d-360">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="9d68d-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="9d68d-361">ケース スタディ、HoloStudio UI および相互作用のデザインの学習</span><span class="sxs-lookup"><span data-stu-id="9d68d-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="9d68d-362">オブジェクトおよび環境のスケール</span><span class="sxs-lookup"><span data-stu-id="9d68d-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="9d68d-363">カーソル、視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="9d68d-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="9d68d-364">外部参照</span><span class="sxs-lookup"><span data-stu-id="9d68d-364">External references</span></span>

* [<span data-ttu-id="9d68d-365">Ado の利用、FOV</span><span class="sxs-lookup"><span data-stu-id="9d68d-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="9d68d-366">コンテンツがユーザーの位置に対応します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-366">Content reacts to user position</span></span>

<span data-ttu-id="9d68d-367">ホログラムは、「実際の」オブジェクトと同じ方法ほぼ内のユーザーの位置に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="9d68d-368">注目すべき設計の考慮事項は、ユーザーの位置を想定できません必ずしも UI 要素が静止していると、ユーザーの動きに合わせては。</span><span class="sxs-lookup"><span data-stu-id="9d68d-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="9d68d-369">ユーザーの位置に正しく対応するアプリをデザインよりかぎりエクスペリエンスの作成し、使いやすきます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-370">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-372"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-373">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-373">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-374">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-375">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9d68d-376">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-376">Best</span></span> </td><td> <span data-ttu-id="9d68d-377">コンテンツと UI は、自然の想定されるユーザーの移動のスコープ内のコンテンツと対話するユーザーを許可するユーザーの位置に適応します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9d68d-378">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-378">Meets</span></span> </td><td> <span data-ttu-id="9d68d-379">UI は、ユーザーの位置に対応しますが、それらの位置を調整するユーザーを必要とするキーのコンテンツの表示を妨げる可能性が。</span><span class="sxs-lookup"><span data-stu-id="9d68d-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9d68d-380">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="9d68d-381">UI 要素が紛失または、移動の原因となるユーザー コントロールを不自然に戻ります (または見つける) 中にロックされています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="9d68d-382">UI 要素は、主要なコンテンツの表示を制限します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="9d68d-383">特に、運動量との距離を表示するため UI の動きが最適化されていない<a href="billboarding-and-tag-along.md">tag-along</a> UI 要素。</span><span class="sxs-lookup"><span data-stu-id="9d68d-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-384">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-384">How to measure</span></span>

* <span data-ttu-id="9d68d-385">すべての測定値は、シナリオの妥当な範囲内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="9d68d-386">ユーザーの移動はによって異なりますが、極端なユーザーの移動は、アプリをください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="9d68d-387">UI 要素、関連するコントロールをユーザーの移動に関係なく利用してください。</span><span class="sxs-lookup"><span data-stu-id="9d68d-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="9d68d-388">たとえば、ユーザーが表示とズームを使用して 3D マップを歩きながら、ズーム コントロールが場所に関係なく、ユーザーにすぐに使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-389">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-389">Recommendations</span></span>

* <span data-ttu-id="9d68d-390">ユーザーは、カメラであり、動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="9d68d-391">ドライブにできるようにします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-391">Let them drive.</span></span>
* <span data-ttu-id="9d68d-392">テキストのためのビルボードを検討してくださいされ帰りシステム world ロックや非表示になる場合、ユーザー、それ以外の場合に移動します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="9d68d-393">前に新機能については、ユーザーを許可する一方、ユーザーをフォローする必要があるコンテンツの tag-along を使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-394">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-395">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-395">Documentation</span></span>

* [<span data-ttu-id="9d68d-396">対話デザイン</span><span class="sxs-lookup"><span data-stu-id="9d68d-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="9d68d-397">色、光、および資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="9d68d-398">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="9d68d-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9d68d-399">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="9d68d-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9d68d-400">自己モーションとユーザー locomotion</span><span class="sxs-lookup"><span data-stu-id="9d68d-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-401">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-401">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-402">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="9d68d-403">入力の相互作用をわかりやすくするため</span><span class="sxs-lookup"><span data-stu-id="9d68d-403">Input interaction clarity</span></span>

<span data-ttu-id="9d68d-404">入力の相互作用をわかりやすくするためは、アプリの有用性に重大な入力の整合性、未成熟、見つけやすさの相互作用の方法が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="9d68d-405">ユーザーは、再確認せずにプラットフォーム全体にわたる一般的な相互作用を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="9d68d-406">アプリにカスタムの入力がある場合が明確に伝達し、説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-407">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-409"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-410">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-410">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-411">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-412">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-412">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-413">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-413">Best</span></span>  |  <span data-ttu-id="9d68d-414">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-414">Meets</span></span> |  <span data-ttu-id="9d68d-415">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-416">入力の対話操作のメソッドは提供されている Windows Mixed Reality で一貫性のある[ガイダンス](interaction-fundamentals.md)します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="9d68d-417">任意のカスタム入力標準入力 (使用して標準的な対話ではなく) と重複することはできません必要があります明確に伝達およびユーザーに示されています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="9d68d-418">同様に最適ですがカスタムの入力は、標準入力方式を冗長です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="9d68d-419">ユーザーの目標とアプリ エクスペリエンスの進行状況を実現できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="9d68d-420">入力メソッドまたはボタンのマッピングを理解するのには困難です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="9d68d-421">入力が大きくカスタマイズされて、なしの手順については、標準の入力をサポートしていませんまたは疲労と快適性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-422">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-422">How to measure</span></span>

* <span data-ttu-id="9d68d-423">アプリで使用する一貫性のある[標準入力方式。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="9d68d-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="9d68d-424">アプリにカスタムの入力がある場合は、それを明確にを通じてを伝達します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="9d68d-425">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="9d68d-425">First-run experience</span></span>
* <span data-ttu-id="9d68d-426">概要画面</span><span class="sxs-lookup"><span data-stu-id="9d68d-426">Introductory screens</span></span>
* <span data-ttu-id="9d68d-427">ヒント</span><span class="sxs-lookup"><span data-stu-id="9d68d-427">Tooltips</span></span>
* <span data-ttu-id="9d68d-428">手動指導者</span><span class="sxs-lookup"><span data-stu-id="9d68d-428">Hand coach</span></span>
* <span data-ttu-id="9d68d-429">ヘルプ セクション</span><span class="sxs-lookup"><span data-stu-id="9d68d-429">Help section</span></span>
* <span data-ttu-id="9d68d-430">ボイス オーバー</span><span class="sxs-lookup"><span data-stu-id="9d68d-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-431">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-431">Recommendations</span></span>

* <span data-ttu-id="9d68d-432">可能な限り標準の入力メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="9d68d-433">標準以外の入力方法のデモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="9d68d-434">アプリ全体で一貫性のある相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-435">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-436">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-436">Documentation</span></span>

* [<span data-ttu-id="9d68d-437">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="9d68d-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9d68d-438">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9d68d-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="9d68d-439">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="9d68d-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9d68d-440">カーソル</span><span class="sxs-lookup"><span data-stu-id="9d68d-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9d68d-441">快適性と視線入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="9d68d-442">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="9d68d-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="9d68d-443">音声入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="9d68d-444">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="9d68d-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="9d68d-445">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9d68d-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="9d68d-446">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="9d68d-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="9d68d-447">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="9d68d-448">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="9d68d-449">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9d68d-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="9d68d-450">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="9d68d-451">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="9d68d-452">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="9d68d-453">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9d68d-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="9d68d-454">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-455">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-455">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-456">ケース スタディ:複数のパーソナル コンピューティングのフォロー アップ</span><span class="sxs-lookup"><span data-stu-id="9d68d-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="9d68d-457">調査をキャストします。HoloStudio UI との対話デザインの学習内容</span><span class="sxs-lookup"><span data-stu-id="9d68d-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="9d68d-458">サンプル アプリ:要素の定期処理テーブル</span><span class="sxs-lookup"><span data-stu-id="9d68d-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="9d68d-459">サンプル アプリ:旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="9d68d-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="9d68d-460">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="9d68d-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="9d68d-461">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="9d68d-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="9d68d-462">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="9d68d-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="9d68d-463">対話型のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9d68d-463">Interactable objects</span></span>

<span data-ttu-id="9d68d-464">ボタンには、2 D 抽象世界でイベントをトリガーに使用されるメタファが長年です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="9d68d-465">3 次元の複合現実の世界では、この抽象化はもはやの世界に限定しました必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="9d68d-466">イベントをトリガーする対話型のオブジェクトを何も指定できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="9d68d-467">対話型のオブジェクトは、そのテーブルに、コーヒー カップから空中に浮かんでバルーンをものとして表現できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="9d68d-468">形式に関係なく対話型のオブジェクトを視覚的およびオーディオをユーザーが明確に認識できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-469">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-471"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-472">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-472">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-473">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-474">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-474">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-475">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-475">Best</span></span>  |  <span data-ttu-id="9d68d-476">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-476">Meets</span></span> |  <span data-ttu-id="9d68d-477">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-478">3 つの状態の間で視覚的およびオーディオを認識できるものは対話型のオブジェクト、形式に関係なく: アイドル状態をターゲットとして、選択します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="9d68d-479">「に言ってを参照してください」がオフで、一貫した使用エクスペリエンスのあらゆる場所。</span><span class="sxs-lookup"><span data-stu-id="9d68d-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="9d68d-480">オブジェクトは拡大縮小され、エラーを対象とする無料のために分散します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="9d68d-481">ユーザーできますオーディオまたはビデオのフィードバックを通じた対話型としてオブジェクトを認識およびできますターゲットし、オブジェクトをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="9d68d-482">ビジュアルやオーディオ キューを指定しない場合は、ユーザーは対話型のオブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="9d68d-483">相互作用は、間違いやすくオブジェクト スケールまたはオブジェクト間の距離が原因です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-484">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-484">How to measure</span></span>

* <span data-ttu-id="9d68d-485">対話型のオブジェクトが '対話型'; として認識できます。特定のボタン、メニューのおよびアプリのコンテンツを含むです。</span><span class="sxs-lookup"><span data-stu-id="9d68d-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="9d68d-486">経験則として必要がありますビジュアルおよびオーディオ キュー対話型のオブジェクトを対象とする場合。</span><span class="sxs-lookup"><span data-stu-id="9d68d-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-487">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-487">Recommendations</span></span>

* <span data-ttu-id="9d68d-488">相互作用のビジュアルおよびオーディオのフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="9d68d-489">それぞれの入力 (アイドル状態、対象となる、選択した) の状態の視覚的なフィードバックを区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="9d68d-490">対話型のオブジェクトを拡張し、エラーを対象とする無料の配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="9d68d-491">(メニュー バーやリスト) グループ化された対話型のオブジェクトには、適切な間隔を対象とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="9d68d-492">音声コマンドをサポートするボタンとメニューは、キーワードのコマンドのテキスト ラベルを指定する必要があります (「表示, に言って」)</span><span class="sxs-lookup"><span data-stu-id="9d68d-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-493">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-494">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-494">Documentation</span></span>

* [<span data-ttu-id="9d68d-495">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9d68d-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9d68d-496">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="9d68d-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="9d68d-497">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="9d68d-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9d68d-498">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="9d68d-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-499">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-499">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-500">Mixed Reality Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="9d68d-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="9d68d-501">ルームのスキャン</span><span class="sxs-lookup"><span data-stu-id="9d68d-501">Room scanning</span></span>

<span data-ttu-id="9d68d-502">空間マッピング データを必要とするアプリでは、時間の経過と共に自動的にこのデータを収集するデバイスに依存しており、ユーザーとセッション間でアクティブなデバイスでの環境について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="9d68d-503">完全を期すため、このデータの品質は、さまざまなユーザーが行った探索の量、探索からどれ時間だけが経過や、デバイス、領域をスキャンするので家具や扉などのオブジェクトが移動するかどうかなどの要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="9d68d-504">多くのアプリでは、ユーザーが、完全を期すためと、空間のマップの品質を向上させるために追加の手順を実行する必要があるかどうかを判断するエクスペリエンスの先頭に空間マッピング データを分析します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="9d68d-505">場合は、ユーザーが、スキャン時にガイダンスが提供される必要があります明確、環境をスキャンするために必要です。</span><span class="sxs-lookup"><span data-stu-id="9d68d-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-506">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-508"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-509">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-509">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-510">❌</span><span class="sxs-lookup"><span data-stu-id="9d68d-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-511">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-511">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-512">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-512">Best</span></span>  |  <span data-ttu-id="9d68d-513">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-513">Meets</span></span> |  <span data-ttu-id="9d68d-514">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-515">空間メッシュの視覚化は、ユーザーのスキャンが進行中に伝えます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="9d68d-516">ユーザーは、対処方法と、スキャンが開始し、停止に明確に認識しています。</span><span class="sxs-lookup"><span data-stu-id="9d68d-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="9d68d-517">空間のメッシュの視覚エフェクトが提供されますが、ユーザーが明確に対処できないを行うと進行状況に関する情報は提供されません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="9d68d-518">メッシュの視覚表現はありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-518">No visualization of mesh.</span></span> <span data-ttu-id="9d68d-519">ガイダンスの情報を探すには、where 句またはときに、スキャンを開始または停止についてユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-520">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-520">How to measure</span></span>

* <span data-ttu-id="9d68d-521">必要なルーム スキャン中に、検索する場所を開始して停止のスキャンを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-522">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-522">Recommendations</span></span>

* <span data-ttu-id="9d68d-523">エクスペリエンスの一部である必要があるユーザーの近くの合計ボリュームの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="9d68d-524">スキャンが開始され、進行状況インジケーターなどを停止すると通信します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="9d68d-525">スキャン中に、メッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="9d68d-526">検索し、ルーム内を移動するユーザーを促すビジュアルおよびオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="9d68d-527">データを向上させるために移動する場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="9d68d-528">多くの場合に必要な内容の操作を行います (例: を見て、ceiling 見て家具の背後にある)、ユーザーに伝えるための最適な場合があります、スキャンのために必要な品質を取得するためにします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-529">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9d68d-530">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="9d68d-530">Documentation</span></span>

* [<span data-ttu-id="9d68d-531">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="9d68d-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="9d68d-532">ケース スタディ:HoloLens の空間のマッピング機能を展開します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9d68d-533">ケース スタディ:空間 HoloTour の設計</span><span class="sxs-lookup"><span data-stu-id="9d68d-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9d68d-534">ケース スタディ:フラグメントで魅力的なエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9d68d-535">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="9d68d-535">Tools and tutorials</span></span>

* [<span data-ttu-id="9d68d-536">Mixed Reality Toolkit - UX</span><span class="sxs-lookup"><span data-stu-id="9d68d-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="9d68d-537">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="9d68d-537">Directional indicators</span></span>

<span data-ttu-id="9d68d-538">Mixed reality アプリでは、コンテンツは、ビューのフィールドの外側にありますか、現実世界のオブジェクトによってオクルー ジョンします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="9d68d-539">適切に設計されたアプリは簡単に表示されているコンテンツを検索するユーザー。</span><span class="sxs-lookup"><span data-stu-id="9d68d-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="9d68d-540">方向インジケーターは、重要なコンテンツをユーザーに警告し、ユーザーの位置を基準としたコンテンツへのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="9d68d-541">非表示のコンテンツへのガイダンスには、サウンドのエミッタ、方向矢印、または直接の視覚的な手掛かりのフォームを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-542">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-544"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-545">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-545">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-546">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-547">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-547">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-548">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-548">Best</span></span>  |  <span data-ttu-id="9d68d-549">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-549">Meets</span></span> |  <span data-ttu-id="9d68d-550">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-551">ビジュアルおよびオーディオ キューは、ビューのフィールドの外側の関連するコンテンツに直接ユーザーを説明します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="9d68d-552">矢印またはコンテンツの全体的な方向性で、ユーザーを示すいくつかのインジケーター。</span><span class="sxs-lookup"><span data-stu-id="9d68d-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="9d68d-553">関連するコンテンツが視野、外部と低いか、ユーザーに場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-554">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-554">How to measure</span></span>

* <span data-ttu-id="9d68d-555">ビューのユーザー フィールドの外部で関連するコンテンツでは、ビジュアルおよびオーディオ キューを検出します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-556">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-556">Recommendations</span></span>

* <span data-ttu-id="9d68d-557">関連するコンテンツは、外部のユーザーのフィールドの表示が、コンテンツにユーザーをガイドするのに方向インジケーターとオーディオ キューを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="9d68d-558">多くの場合、直接 visual ガイドことをお勧め方向矢印にします。</span><span class="sxs-lookup"><span data-stu-id="9d68d-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="9d68d-559">方向インジケーターは、カーソルに組み込まないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-560">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-560">Resources</span></span>

* [<span data-ttu-id="9d68d-561">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="9d68d-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="9d68d-562">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="9d68d-562">Data loading</span></span>

<span data-ttu-id="9d68d-563">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="9d68d-564">ユーザーは、進行状況インジケーターが表示されると、待機時間はどれくらいの時間ありますを示すことも、アプリで操作できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9d68d-565">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="9d68d-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9d68d-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9d68d-567"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9d68d-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9d68d-568">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-568">✔️</span></span></td>
        <td><span data-ttu-id="9d68d-569">✔️</span><span class="sxs-lookup"><span data-stu-id="9d68d-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9d68d-570">品質基準</span><span class="sxs-lookup"><span data-stu-id="9d68d-570">Quality criteria</span></span>

|  <span data-ttu-id="9d68d-571">最高</span><span class="sxs-lookup"><span data-stu-id="9d68d-571">Best</span></span>  |  <span data-ttu-id="9d68d-572">満たす</span><span class="sxs-lookup"><span data-stu-id="9d68d-572">Meets</span></span> |  <span data-ttu-id="9d68d-573">失敗</span><span class="sxs-lookup"><span data-stu-id="9d68d-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9d68d-574">進行状況バーや任意のデータの読み込みまたは処理中に進行状況を示すリングの形式で、視覚的なインジケーターをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="9d68d-575">視覚インジケータは、どのくらいの時間待機する可能性がありますにガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="9d68d-576">データの読み込みが進行中ではどのくらいの時間、待機できることを示す値はありませんが、ユーザーが通知されます。</span><span class="sxs-lookup"><span data-stu-id="9d68d-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="9d68d-577">データの読み込みまたはプロセスのインジケーターを 5 秒以上かかったタスクがありません。</span><span class="sxs-lookup"><span data-stu-id="9d68d-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9d68d-578">測定する方法</span><span class="sxs-lookup"><span data-stu-id="9d68d-578">How to measure</span></span>

* <span data-ttu-id="9d68d-579">データの読み込み中には、5 秒以上の空の状態はありませんを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9d68d-580">推奨事項</span><span class="sxs-lookup"><span data-stu-id="9d68d-580">Recommendations</span></span>

* <span data-ttu-id="9d68d-581">ユーザーがこのアプリが停止しているか、クラッシュするを感じる可能性がある場合に、どのような状況で進行状況を示すデータ読み込み animator を提供します。</span><span class="sxs-lookup"><span data-stu-id="9d68d-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="9d68d-582">妥当な経験則は、'ロード' アクティビティで 5 秒以上かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d68d-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="9d68d-583">参考資料</span><span class="sxs-lookup"><span data-stu-id="9d68d-583">Resources</span></span>

* [<span data-ttu-id="9d68d-584">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="9d68d-584">Displaying progress</span></span>](progress.md)
