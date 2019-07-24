---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024496"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="86238-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-104">App quality criteria</span></span>

<span data-ttu-id="86238-105">このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="86238-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="86238-106">各要素について、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="86238-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="86238-107">[概要] –品質要因とそれが重要な理由について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="86238-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="86238-108">デバイスの影響: Mixed Reality デバイスに影響を与えるウィンドウの種類。</span><span class="sxs-lookup"><span data-stu-id="86238-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="86238-109">品質基準–品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="86238-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="86238-110">方法: 問題を測定 (または経験) する方法。</span><span class="sxs-lookup"><span data-stu-id="86238-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="86238-111">推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="86238-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="86238-112">リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。</span><span class="sxs-lookup"><span data-stu-id="86238-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="86238-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="86238-113">Frame rate</span></span>

<span data-ttu-id="86238-114">フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。</span><span class="sxs-lookup"><span data-stu-id="86238-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="86238-115">推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="86238-116">Windows Mixed Reality イマーシブヘッドセットのエクスペリエンスの目標フレームレートは、サポートする Windows Mixed Reality 互換 Pc に応じて、60Hz または90Hz になります。</span><span class="sxs-lookup"><span data-stu-id="86238-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="86238-117">HoloLens の場合、ターゲットフレームレートは60Hz です。</span><span class="sxs-lookup"><span data-stu-id="86238-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-121">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-121">✔️</span></span></td>
        <td><span data-ttu-id="86238-122">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-123">Quality criteria</span></span>

|  <span data-ttu-id="86238-124">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-124">Best</span></span>  |  <span data-ttu-id="86238-125">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-125">Meets</span></span> |  <span data-ttu-id="86238-126">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="86238-127">アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています。HoloLens の60fpsウルトラ Pc 上の90fpsメインストリーム Pc では60fps。</span><span class="sxs-lookup"><span data-stu-id="86238-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="86238-128">アプリは、コアエクスペリエンスを妨げるすることなく、断続的にフレームを削除します。または FPS は、必要な目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="86238-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="86238-129">アプリでは、平均で10秒以内にフレームレートのドロップが発生しています。</span><span class="sxs-lookup"><span data-stu-id="86238-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="86238-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-130">How to measure</span></span>

* <span data-ttu-id="86238-131">リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance)によって "システムパフォーマンス" によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="86238-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="86238-132">開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="86238-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="86238-133">「サンプルカウンターのリソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86238-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="86238-134">フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="86238-135">ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-136">Recommendations</span></span>

* <span data-ttu-id="86238-137">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="86238-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="86238-138">フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-139">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-140">Documentation</span></span>

* [<span data-ttu-id="86238-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="86238-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="86238-142">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="86238-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="86238-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="86238-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="86238-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-145">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-146">MRToolkit、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="86238-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="86238-147">MRToolkit、シェーダー</span><span class="sxs-lookup"><span data-stu-id="86238-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="86238-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="86238-148">External references</span></span>

* [<span data-ttu-id="86238-149">Unity, モバイルアプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="86238-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="86238-150">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="86238-150">Hologram stability</span></span>

<span data-ttu-id="86238-151">安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="86238-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="86238-152">ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。</span><span class="sxs-lookup"><span data-stu-id="86238-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="86238-153">フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="86238-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="86238-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="86238-155">空間アンカーへの距離</span><span class="sxs-lookup"><span data-stu-id="86238-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="86238-156">Tracking</span><span class="sxs-lookup"><span data-stu-id="86238-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-159"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-160">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-160">✔️</span></span></td>
        <td><span data-ttu-id="86238-161">❌</span><span class="sxs-lookup"><span data-stu-id="86238-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-162">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-162">Quality criteria</span></span>

|  <span data-ttu-id="86238-163">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-163">Best</span></span>  |  <span data-ttu-id="86238-164">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-164">Meets</span></span> |  <span data-ttu-id="86238-165">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-166">ホログラムは常に安定した状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="86238-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="86238-167">セカンダリコンテンツは予期しない移動を示すまたは、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="86238-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="86238-168">フレーム内のプライマリコンテンツは、予期しない移動を示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="86238-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="86238-169">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-169">How to measure</span></span>

<span data-ttu-id="86238-170">デバイスを装着し、エクスペリエンスを表示しています。</span><span class="sxs-lookup"><span data-stu-id="86238-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="86238-171">ヘッドを左右に移動します。ホログラムが予期しない動きを示している場合は、フレームレートが低いか、または安定性平面が焦点平面に正しく配置されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="86238-172">ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="86238-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="86238-173">この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="86238-174">フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="86238-175">な推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-175">Recomendations</span></span>

* <span data-ttu-id="86238-176">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="86238-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="86238-177">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="86238-178">アンカーの3メートル以内に固定したホログラムを常にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="86238-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="86238-179">環境が適切に追跡できるようにセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="86238-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="86238-180">フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="86238-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-181">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-182">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-182">Documentation</span></span>

* [<span data-ttu-id="86238-183">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="86238-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="86238-184">安定化平面を使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="86238-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="86238-185">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="86238-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="86238-186">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="86238-187">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="86238-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="86238-188">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="86238-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="86238-189">静止フレーム (参照)</span><span class="sxs-lookup"><span data-stu-id="86238-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-190">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-190">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-191">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="86238-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="86238-192">実際のサーフェイス上のホログラムの位置</span><span class="sxs-lookup"><span data-stu-id="86238-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="86238-193">物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="86238-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="86238-194">配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-195">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-197"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-198">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-198">✔️</span></span></td>
        <td><span data-ttu-id="86238-199">❌</span><span class="sxs-lookup"><span data-stu-id="86238-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-200">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-200">Quality criteria</span></span>

|  <span data-ttu-id="86238-201">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-201">Best</span></span>  |  <span data-ttu-id="86238-202">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-202">Meets</span></span> |  <span data-ttu-id="86238-203">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="86238-204">ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="86238-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="86238-205">より正確な要件が必要な場合は、アプリが目的のアプリ仕様内でコラボレーションのための効率的な手段を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="86238-206">NA</span><span class="sxs-lookup"><span data-stu-id="86238-206">NA</span></span> | <span data-ttu-id="86238-207">サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。</span><span class="sxs-lookup"><span data-stu-id="86238-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="86238-208">精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-209">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-209">How to measure</span></span>

* <span data-ttu-id="86238-210">空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="86238-211">正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。</span><span class="sxs-lookup"><span data-stu-id="86238-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-212">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-212">Recommendations</span></span>

* <span data-ttu-id="86238-213">空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="86238-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="86238-214">最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。</span><span class="sxs-lookup"><span data-stu-id="86238-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="86238-215">特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="86238-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="86238-216">不適切に設定した interpupilary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="86238-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="86238-217">常に HoloLens をユーザーの IPD に構成します。</span><span class="sxs-lookup"><span data-stu-id="86238-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-218">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-219">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-219">Documentation</span></span>

* [<span data-ttu-id="86238-220">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="86238-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="86238-221">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="86238-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="86238-222">空間アンカーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="86238-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="86238-223">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="86238-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="86238-224">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="86238-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="86238-225">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="86238-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-226">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-226">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-227">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="86238-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="86238-228">MR ツールキット, 空間マッピングライブラリ</span><span class="sxs-lookup"><span data-stu-id="86238-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="86238-229">MR コンパニオンキット、ポスター調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="86238-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="86238-230">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="86238-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="86238-231">外部参照</span><span class="sxs-lookup"><span data-stu-id="86238-231">External references</span></span>

* [<span data-ttu-id="86238-232">Lowes のケーススタディ、有効桁数のアラインメント</span><span class="sxs-lookup"><span data-stu-id="86238-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="86238-233">快適なゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="86238-233">Viewing zone of comfort</span></span>

<span data-ttu-id="86238-234">アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="86238-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="86238-235">Hololens のディスプレイは、ユーザーから約2.0 分離れた光学距離で固定されているため、HoloLens を装着したユーザーは常に 2.0 m に対応して明確なイメージを維持します。</span><span class="sxs-lookup"><span data-stu-id="86238-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="86238-236">不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-237">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-239"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-240">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-240">✔️</span></span></td>
        <td><span data-ttu-id="86238-241">❌</span><span class="sxs-lookup"><span data-stu-id="86238-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-242">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="86238-243">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="86238-244">コンテンツを2m に配置します。</span><span class="sxs-lookup"><span data-stu-id="86238-244">Place content at 2m.</span></span></li><li><span data-ttu-id="86238-245">ホログラムを2m に配置できず、収束と設備の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m と5分の間になります。</span><span class="sxs-lookup"><span data-stu-id="86238-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="86238-246">どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</span><span class="sxs-lookup"><span data-stu-id="86238-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="86238-247">シナリオで特に要求されていない限り、クリッププレーンは1m から始まる fadeout で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="86238-248">Motionless ホログラムの詳細な監視が必要な場合は、コンテンツを50cm より近くにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="86238-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="86238-249">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-249">Meets</span></span></td><td> <span data-ttu-id="86238-250">コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</span><span class="sxs-lookup"><span data-stu-id="86238-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86238-251">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-251">Fail</span></span> </td><td> <span data-ttu-id="86238-252">コンテンツが非常に近い場所に&lt;表示されます&lt;(通常は 1.25 m、またはより詳細な監視が必要な固定のホログラムの場合は 50cm)。</span><span class="sxs-lookup"><span data-stu-id="86238-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="86238-253">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-253">How to measure</span></span>

* <span data-ttu-id="86238-254">通常、コンテンツは2m である必要がありますが、1.25 以上、5分を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="86238-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="86238-255">例外がいくつかある場合は、1 m から開始したコンテンツの fadeout を使用して、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="86238-256">コンテンツにアプローチし、クリッピング平面効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="86238-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="86238-257">静止コンテンツは、50cm を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="86238-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-258">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-258">Recommendations</span></span>

* <span data-ttu-id="86238-259">最適な表示距離が2m のコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="86238-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="86238-260">1m からのコンテンツの fadeout を使用して、クリッピングレンダリング距離を85cm に設定します。</span><span class="sxs-lookup"><span data-stu-id="86238-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="86238-261">近くに表示する必要がある固定のホログラムの場合、クリッピングプレーンは30cm 以下で、fadeout はクリッピング平面から少なくとも10cm 離れた位置にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-262">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-262">Resources</span></span>

* [<span data-ttu-id="86238-263">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="86238-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="86238-264">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="86238-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="86238-265">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="86238-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="86238-266">テキスト、推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="86238-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="86238-267">深度の切り替え</span><span class="sxs-lookup"><span data-stu-id="86238-267">Depth switching</span></span>

<span data-ttu-id="86238-268">快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-269">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-271"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-272">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-272">✔️</span></span></td>
        <td><span data-ttu-id="86238-273">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-274">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-274">Quality criteria</span></span>

|  <span data-ttu-id="86238-275">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-275">Best</span></span>  |  <span data-ttu-id="86238-276">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-276">Meets</span></span> |  <span data-ttu-id="86238-277">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-278">ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="86238-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="86238-279">[突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。</span><span class="sxs-lookup"><span data-stu-id="86238-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="86238-280">一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="86238-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-281">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-281">How to measure</span></span>

* <span data-ttu-id="86238-282">アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。</span><span class="sxs-lookup"><span data-stu-id="86238-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-283">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-283">Recommendations</span></span>

* <span data-ttu-id="86238-284">一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="86238-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="86238-285">これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="86238-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-286">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-286">Resources</span></span>

* [<span data-ttu-id="86238-287">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="86238-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="86238-288">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="86238-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="86238-289">空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="86238-289">Use of spatial sound</span></span>

<span data-ttu-id="86238-290">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="86238-291">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) でサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="86238-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="86238-292">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="86238-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="86238-293">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="86238-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-294">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-296"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-297">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-297">✔️</span></span></td>
        <td><span data-ttu-id="86238-298">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-299">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-299">Quality criteria</span></span>

|  <span data-ttu-id="86238-300">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-300">Best</span></span>  |  <span data-ttu-id="86238-301">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-301">Meets</span></span> |  <span data-ttu-id="86238-302">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-303">サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。</span><span class="sxs-lookup"><span data-stu-id="86238-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="86238-304">サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="86238-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="86238-305">空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。</span><span class="sxs-lookup"><span data-stu-id="86238-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="86238-306">サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。</span><span class="sxs-lookup"><span data-stu-id="86238-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="86238-307">または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="86238-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-308">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-308">How to measure</span></span>

* <span data-ttu-id="86238-309">一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。</span><span class="sxs-lookup"><span data-stu-id="86238-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="86238-310">サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-311">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-311">Recommendations</span></span>

* <span data-ttu-id="86238-312">オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="86238-313">実際のサウンドは、合成や不自然な音よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="86238-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="86238-314">ほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="86238-315">非表示の発信器は避けてください。</span><span class="sxs-lookup"><span data-stu-id="86238-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="86238-316">空間マスクは避けてください。</span><span class="sxs-lookup"><span data-stu-id="86238-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="86238-317">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="86238-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-318">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-319">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-319">Documentation</span></span>

* [<span data-ttu-id="86238-320">立体音響</span><span class="sxs-lookup"><span data-stu-id="86238-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="86238-321">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="86238-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="86238-322">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="86238-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="86238-323">ケーススタディ、HoloTour の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="86238-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="86238-324">RoboRaid の空間サウンドを使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="86238-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-325">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-325">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-326">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="86238-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="86238-327">MRToolkit、空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="86238-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="86238-328">Holographic frame (視界) の境界にフォーカス</span><span class="sxs-lookup"><span data-stu-id="86238-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="86238-329">適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。</span><span class="sxs-lookup"><span data-stu-id="86238-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="86238-330">視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="86238-331">そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="86238-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-332">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-334"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-335">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-335">✔️</span></span></td>
        <td><span data-ttu-id="86238-336">❌</span><span class="sxs-lookup"><span data-stu-id="86238-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-337">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-337">Quality criteria</span></span>

|  <span data-ttu-id="86238-338">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-338">Best</span></span>  |  <span data-ttu-id="86238-339">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-339">Meets</span></span> |  <span data-ttu-id="86238-340">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-341">ユーザーはコンテキストを失うことはなく、表示も快適です。</span><span class="sxs-lookup"><span data-stu-id="86238-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="86238-342">ラージオブジェクトのコンテキストに関するサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="86238-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="86238-343">フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="86238-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="86238-344">一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。</span><span class="sxs-lookup"><span data-stu-id="86238-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="86238-345">ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="86238-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="86238-346">限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="86238-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="86238-347">ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="86238-348">大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="86238-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-349">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-349">How to measure</span></span>

* <span data-ttu-id="86238-350">境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。</span><span class="sxs-lookup"><span data-stu-id="86238-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="86238-351">ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。</span><span class="sxs-lookup"><span data-stu-id="86238-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="86238-352">シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。</span><span class="sxs-lookup"><span data-stu-id="86238-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-353">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-353">Recommendations</span></span>

* <span data-ttu-id="86238-354">視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。</span><span class="sxs-lookup"><span data-stu-id="86238-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="86238-355">空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="86238-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="86238-356">可能な限り、視界を垂直方向にクリップするホログラムは避けてください。</span><span class="sxs-lookup"><span data-stu-id="86238-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="86238-357">ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="86238-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-358">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-359">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-359">Documentation</span></span>

* [<span data-ttu-id="86238-360">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="86238-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="86238-361">ケーススタディ、HoloStudio UI、相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="86238-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="86238-362">オブジェクトと環境のスケール</span><span class="sxs-lookup"><span data-stu-id="86238-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="86238-363">カーソル、ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="86238-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="86238-364">外部参照</span><span class="sxs-lookup"><span data-stu-id="86238-364">External references</span></span>

* [<span data-ttu-id="86238-365">視界に関する多くの ado</span><span class="sxs-lookup"><span data-stu-id="86238-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="86238-366">ユーザーの位置に反応するコンテンツ</span><span class="sxs-lookup"><span data-stu-id="86238-366">Content reacts to user position</span></span>

<span data-ttu-id="86238-367">ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="86238-368">注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。</span><span class="sxs-lookup"><span data-stu-id="86238-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="86238-369">ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="86238-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-370">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-372"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-373">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-373">✔️</span></span></td>
        <td><span data-ttu-id="86238-374">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-375">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="86238-376">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-376">Best</span></span> </td><td> <span data-ttu-id="86238-377">コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</span><span class="sxs-lookup"><span data-stu-id="86238-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86238-378">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-378">Meets</span></span> </td><td> <span data-ttu-id="86238-379">UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86238-380">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="86238-381">UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</span><span class="sxs-lookup"><span data-stu-id="86238-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="86238-382">UI 要素は、プライマリコンテンツのビューを制限します。</span><span class="sxs-lookup"><span data-stu-id="86238-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="86238-383">UI の移動は、特に<a href="billboarding-and-tag-along.md">タグに沿っ</a>た ui 要素によって、距離や勢いを表示するために最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="86238-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="86238-384">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-384">How to measure</span></span>

* <span data-ttu-id="86238-385">すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="86238-386">ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="86238-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="86238-387">UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="86238-388">たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-389">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-389">Recommendations</span></span>

* <span data-ttu-id="86238-390">ユーザーはカメラで、動きを制御します。</span><span class="sxs-lookup"><span data-stu-id="86238-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="86238-391">これらのドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-391">Let them drive.</span></span>
* <span data-ttu-id="86238-392">テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="86238-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="86238-393">ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-394">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-395">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-395">Documentation</span></span>

* [<span data-ttu-id="86238-396">相互作用の設計</span><span class="sxs-lookup"><span data-stu-id="86238-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="86238-397">色、光、素材</span><span class="sxs-lookup"><span data-stu-id="86238-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="86238-398">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="86238-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="86238-399">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="86238-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="86238-400">自己動きとユーザー locomotion</span><span class="sxs-lookup"><span data-stu-id="86238-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-401">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-401">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-402">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="86238-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="86238-403">入力の相互作用のわかりやすさ</span><span class="sxs-lookup"><span data-stu-id="86238-403">Input interaction clarity</span></span>

<span data-ttu-id="86238-404">入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86238-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="86238-405">ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="86238-406">アプリにカスタム入力がある場合は、それを明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="86238-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-407">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-409"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-410">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-410">✔️</span></span></td>
        <td><span data-ttu-id="86238-411">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-412">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-412">Quality criteria</span></span>

|  <span data-ttu-id="86238-413">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-413">Best</span></span>  |  <span data-ttu-id="86238-414">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-414">Meets</span></span> |  <span data-ttu-id="86238-415">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-416">入力の相互作用メソッドは、Windows Mixed Reality に用意されている[ガイダンス](interaction-fundamentals.md)と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="86238-417">任意のカスタム入力を標準入力で冗長にする (標準の対話を使用する) ことはできません。また、ユーザーに明確に通知してデモンストレーションする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="86238-418">"最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。</span><span class="sxs-lookup"><span data-stu-id="86238-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="86238-419">ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。</span><span class="sxs-lookup"><span data-stu-id="86238-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="86238-420">入力方法またはボタンのマッピングを理解するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="86238-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="86238-421">入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="86238-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-422">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-422">How to measure</span></span>

* <span data-ttu-id="86238-423">アプリでは、一貫[した標準の入力方法が使用されます。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="86238-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="86238-424">アプリになる入力がある場合は、次の方法で明確に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="86238-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="86238-425">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="86238-425">First-run experience</span></span>
* <span data-ttu-id="86238-426">入門画面</span><span class="sxs-lookup"><span data-stu-id="86238-426">Introductory screens</span></span>
* <span data-ttu-id="86238-427">ツールヒント</span><span class="sxs-lookup"><span data-stu-id="86238-427">Tooltips</span></span>
* <span data-ttu-id="86238-428">手コーチ</span><span class="sxs-lookup"><span data-stu-id="86238-428">Hand coach</span></span>
* <span data-ttu-id="86238-429">ヘルプセクション</span><span class="sxs-lookup"><span data-stu-id="86238-429">Help section</span></span>
* <span data-ttu-id="86238-430">ボイスオーバー</span><span class="sxs-lookup"><span data-stu-id="86238-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-431">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-431">Recommendations</span></span>

* <span data-ttu-id="86238-432">可能な場合は常に標準の入力方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="86238-433">標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="86238-434">アプリ全体で一貫した相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-435">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-436">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-436">Documentation</span></span>

* [<span data-ttu-id="86238-437">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="86238-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="86238-438">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="86238-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="86238-439">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="86238-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="86238-440">カーソル</span><span class="sxs-lookup"><span data-stu-id="86238-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="86238-441">快適で見つめ</span><span class="sxs-lookup"><span data-stu-id="86238-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="86238-442">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="86238-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="86238-443">音声入力</span><span class="sxs-lookup"><span data-stu-id="86238-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="86238-444">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="86238-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="86238-445">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="86238-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="86238-446">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="86238-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="86238-447">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="86238-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="86238-448">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="86238-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="86238-449">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="86238-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="86238-450">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="86238-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="86238-451">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="86238-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="86238-452">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="86238-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="86238-453">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="86238-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="86238-454">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="86238-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-455">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-455">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-456">ケーススタディ:よりパーソナルコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="86238-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="86238-457">キャストスタディ:HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="86238-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="86238-458">サンプルアプリ:要素の周期テーブル</span><span class="sxs-lookup"><span data-stu-id="86238-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="86238-459">サンプルアプリ:旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="86238-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="86238-460">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="86238-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="86238-461">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="86238-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="86238-462">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="86238-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="86238-463">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="86238-463">Interactable objects</span></span>

<span data-ttu-id="86238-464">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="86238-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="86238-465">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="86238-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="86238-466">イベントをトリガーする対話型オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="86238-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="86238-467">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="86238-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="86238-468">フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-469">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-471"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-472">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-472">✔️</span></span></td>
        <td><span data-ttu-id="86238-473">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-474">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-474">Quality criteria</span></span>

|  <span data-ttu-id="86238-475">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-475">Best</span></span>  |  <span data-ttu-id="86238-476">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-476">Meets</span></span> |  <span data-ttu-id="86238-477">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-478">フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。</span><span class="sxs-lookup"><span data-stu-id="86238-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="86238-479">"ご覧のように、エクスペリエンス全体で一貫して使用されています。</span><span class="sxs-lookup"><span data-stu-id="86238-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="86238-480">オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。</span><span class="sxs-lookup"><span data-stu-id="86238-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="86238-481">ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="86238-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="86238-482">ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="86238-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="86238-483">オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="86238-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-484">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-484">How to measure</span></span>

* <span data-ttu-id="86238-485">対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。</span><span class="sxs-lookup"><span data-stu-id="86238-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="86238-486">経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。</span><span class="sxs-lookup"><span data-stu-id="86238-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-487">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-487">Recommendations</span></span>

* <span data-ttu-id="86238-488">対話のためにビジュアルとオーディオフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="86238-489">視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります</span><span class="sxs-lookup"><span data-stu-id="86238-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="86238-490">対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="86238-491">グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="86238-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="86238-492">音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。</span><span class="sxs-lookup"><span data-stu-id="86238-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="86238-493">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-494">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-494">Documentation</span></span>

* [<span data-ttu-id="86238-495">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="86238-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="86238-496">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="86238-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="86238-497">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="86238-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="86238-498">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="86238-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-499">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-499">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-500">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="86238-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="86238-501">部屋のスキャン</span><span class="sxs-lookup"><span data-stu-id="86238-501">Room scanning</span></span>

<span data-ttu-id="86238-502">空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="86238-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="86238-503">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="86238-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="86238-504">多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="86238-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="86238-505">ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86238-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-506">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-508"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-509">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-509">✔️</span></span></td>
        <td><span data-ttu-id="86238-510">❌</span><span class="sxs-lookup"><span data-stu-id="86238-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-511">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-511">Quality criteria</span></span>

|  <span data-ttu-id="86238-512">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-512">Best</span></span>  |  <span data-ttu-id="86238-513">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-513">Meets</span></span> |  <span data-ttu-id="86238-514">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-515">ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。</span><span class="sxs-lookup"><span data-stu-id="86238-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="86238-516">ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。</span><span class="sxs-lookup"><span data-stu-id="86238-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="86238-517">空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86238-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="86238-518">メッシュの視覚化がありません。</span><span class="sxs-lookup"><span data-stu-id="86238-518">No visualization of mesh.</span></span> <span data-ttu-id="86238-519">検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。</span><span class="sxs-lookup"><span data-stu-id="86238-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="86238-520">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-520">How to measure</span></span>

* <span data-ttu-id="86238-521">必要なルームスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="86238-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-522">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-522">Recommendations</span></span>

* <span data-ttu-id="86238-523">ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="86238-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="86238-524">スキャンが開始され、進行状況インジケーターなどの停止時に通信します。</span><span class="sxs-lookup"><span data-stu-id="86238-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="86238-525">スキャン中にメッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="86238-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="86238-526">ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="86238-527">データを改善するための場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="86238-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="86238-528">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="86238-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-529">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="86238-530">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="86238-530">Documentation</span></span>

* [<span data-ttu-id="86238-531">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="86238-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="86238-532">ケーススタディ:HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="86238-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="86238-533">ケーススタディ:HoloTour の空間サウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="86238-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="86238-534">ケーススタディ:フラグメントでのイマーシブエクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="86238-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="86238-535">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="86238-535">Tools and tutorials</span></span>

* [<span data-ttu-id="86238-536">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="86238-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="86238-537">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="86238-537">Directional indicators</span></span>

<span data-ttu-id="86238-538">Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="86238-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="86238-539">適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。</span><span class="sxs-lookup"><span data-stu-id="86238-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="86238-540">ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="86238-541">非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。</span><span class="sxs-lookup"><span data-stu-id="86238-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-542">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-544"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-545">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-545">✔️</span></span></td>
        <td><span data-ttu-id="86238-546">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-547">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-547">Quality criteria</span></span>

|  <span data-ttu-id="86238-548">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-548">Best</span></span>  |  <span data-ttu-id="86238-549">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-549">Meets</span></span> |  <span data-ttu-id="86238-550">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-551">ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。</span><span class="sxs-lookup"><span data-stu-id="86238-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="86238-552">コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。</span><span class="sxs-lookup"><span data-stu-id="86238-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="86238-553">関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="86238-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="86238-554">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-554">How to measure</span></span>

* <span data-ttu-id="86238-555">ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="86238-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-556">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-556">Recommendations</span></span>

* <span data-ttu-id="86238-557">関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。</span><span class="sxs-lookup"><span data-stu-id="86238-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="86238-558">多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="86238-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="86238-559">方向インジケーターをカーソルに組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="86238-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-560">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-560">Resources</span></span>

* [<span data-ttu-id="86238-561">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="86238-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="86238-562">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="86238-562">Data loading</span></span>

<span data-ttu-id="86238-563">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="86238-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="86238-564">これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="86238-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="86238-565">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="86238-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="86238-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="86238-567"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="86238-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="86238-568">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-568">✔️</span></span></td>
        <td><span data-ttu-id="86238-569">✔️</span><span class="sxs-lookup"><span data-stu-id="86238-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="86238-570">品質基準</span><span class="sxs-lookup"><span data-stu-id="86238-570">Quality criteria</span></span>

|  <span data-ttu-id="86238-571">合っ</span><span class="sxs-lookup"><span data-stu-id="86238-571">Best</span></span>  |  <span data-ttu-id="86238-572">あっ</span><span class="sxs-lookup"><span data-stu-id="86238-572">Meets</span></span> |  <span data-ttu-id="86238-573">オーバー</span><span class="sxs-lookup"><span data-stu-id="86238-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="86238-574">データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。</span><span class="sxs-lookup"><span data-stu-id="86238-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="86238-575">ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="86238-576">ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="86238-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="86238-577">タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。</span><span class="sxs-lookup"><span data-stu-id="86238-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="86238-578">測定する方法</span><span class="sxs-lookup"><span data-stu-id="86238-578">How to measure</span></span>

* <span data-ttu-id="86238-579">データの読み込み中に、5秒を超える空の状態がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="86238-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="86238-580">推奨事項</span><span class="sxs-lookup"><span data-stu-id="86238-580">Recommendations</span></span>

* <span data-ttu-id="86238-581">ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="86238-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="86238-582">目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="86238-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="86238-583">リソース</span><span class="sxs-lookup"><span data-stu-id="86238-583">Resources</span></span>

* [<span data-ttu-id="86238-584">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="86238-584">Displaying progress</span></span>](progress.md)
