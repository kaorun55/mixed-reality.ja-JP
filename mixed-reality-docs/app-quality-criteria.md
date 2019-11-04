---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437047"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="ba067-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-104">App quality criteria</span></span>

<span data-ttu-id="ba067-105">このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba067-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="ba067-106">各要素について、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="ba067-107">[概要] –品質要因とそれが重要な理由について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="ba067-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="ba067-108">デバイスの影響: Mixed Reality デバイスに影響を与えるウィンドウの種類。</span><span class="sxs-lookup"><span data-stu-id="ba067-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="ba067-109">品質基準–品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="ba067-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="ba067-110">方法: 問題を測定 (または経験) する方法。</span><span class="sxs-lookup"><span data-stu-id="ba067-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="ba067-111">推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="ba067-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="ba067-112">リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。</span><span class="sxs-lookup"><span data-stu-id="ba067-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="ba067-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="ba067-113">Frame rate</span></span>

<span data-ttu-id="ba067-114">フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。</span><span class="sxs-lookup"><span data-stu-id="ba067-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="ba067-115">推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="ba067-116">Windows Mixed Reality イマーシブヘッドセットのエクスペリエンスの目標フレームレートは、サポートする Windows Mixed Reality 互換 Pc に応じて、60Hz または90Hz になります。</span><span class="sxs-lookup"><span data-stu-id="ba067-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="ba067-117">HoloLens の場合、ターゲットフレームレートは60Hz です。</span><span class="sxs-lookup"><span data-stu-id="ba067-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-120"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-121">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-121">✔️</span></span></td>
        <td><span data-ttu-id="ba067-122">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-123">Quality criteria</span></span>

|  <span data-ttu-id="ba067-124">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-124">Best</span></span>  |  <span data-ttu-id="ba067-125">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-125">Meets</span></span> |  <span data-ttu-id="ba067-126">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="ba067-127">アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています: HoloLens の60fpsウルトラ Pc 上の90fpsメインストリーム Pc では60fps。</span><span class="sxs-lookup"><span data-stu-id="ba067-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="ba067-128">アプリは、コアエクスペリエンスを妨げるすることなく、断続的にフレームを削除します。または FPS は、必要な目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="ba067-129">アプリでは、平均で10秒以内にフレームレートのドロップが発生しています。</span><span class="sxs-lookup"><span data-stu-id="ba067-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ba067-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-130">How to measure</span></span>

* <span data-ttu-id="ba067-131">リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance)によって "システムパフォーマンス" によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="ba067-132">開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="ba067-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="ba067-133">「サンプルカウンターのリソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba067-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="ba067-134">フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="ba067-135">ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-136">Recommendations</span></span>

* <span data-ttu-id="ba067-137">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba067-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="ba067-138">フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-139">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-140">Documentation</span></span>

* [<span data-ttu-id="ba067-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="ba067-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="ba067-142">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="ba067-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="ba067-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="ba067-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="ba067-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-145">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-146">MRToolkit、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="ba067-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="ba067-147">MRToolkit、シェーダー</span><span class="sxs-lookup"><span data-stu-id="ba067-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="ba067-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="ba067-148">External references</span></span>

* [<span data-ttu-id="ba067-149">Unity, モバイルアプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="ba067-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="ba067-150">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="ba067-150">Hologram stability</span></span>

<span data-ttu-id="ba067-151">安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba067-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="ba067-152">ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。</span><span class="sxs-lookup"><span data-stu-id="ba067-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="ba067-153">フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="ba067-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="ba067-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="ba067-155">空間アンカーへの距離</span><span class="sxs-lookup"><span data-stu-id="ba067-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="ba067-156">追跡</span><span class="sxs-lookup"><span data-stu-id="ba067-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-159"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-160">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-161">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-161">Quality criteria</span></span>

|  <span data-ttu-id="ba067-162">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-162">Best</span></span>  |  <span data-ttu-id="ba067-163">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-163">Meets</span></span> |  <span data-ttu-id="ba067-164">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-165">ホログラムは常に安定した状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="ba067-166">セカンダリコンテンツは予期しない移動を示すまたは、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="ba067-167">フレーム内のプライマリコンテンツは、予期しない移動を示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="ba067-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ba067-168">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-168">How to measure</span></span>

<span data-ttu-id="ba067-169">デバイスを装着し、エクスペリエンスを表示しています。</span><span class="sxs-lookup"><span data-stu-id="ba067-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="ba067-170">ヘッドを左右に移動します。ホログラムが予期しない動きを示している場合は、フレームレートが低いか、または安定性平面が焦点平面に正しく配置されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="ba067-171">ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="ba067-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="ba067-172">この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="ba067-173">フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="ba067-174">な推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-174">Recomendations</span></span>

* <span data-ttu-id="ba067-175">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba067-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="ba067-176">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="ba067-177">アンカーの3メートル以内に固定したホログラムを常にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="ba067-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="ba067-178">環境が適切に追跡できるようにセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba067-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="ba067-179">フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="ba067-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-180">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-181">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-181">Documentation</span></span>

* [<span data-ttu-id="ba067-182">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="ba067-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="ba067-183">安定化平面を使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="ba067-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="ba067-184">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="ba067-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="ba067-185">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="ba067-186">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="ba067-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="ba067-187">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="ba067-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="ba067-188">静止フレーム (参照)</span><span class="sxs-lookup"><span data-stu-id="ba067-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-189">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-189">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-190">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="ba067-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="ba067-191">実際のサーフェイス上のホログラムの位置</span><span class="sxs-lookup"><span data-stu-id="ba067-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="ba067-192">物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="ba067-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="ba067-193">配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-194">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-196"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-197">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-198">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-198">Quality criteria</span></span>

|  <span data-ttu-id="ba067-199">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-199">Best</span></span>  |  <span data-ttu-id="ba067-200">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-200">Meets</span></span> |  <span data-ttu-id="ba067-201">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="ba067-202">ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="ba067-203">より正確な要件が必要な場合は、アプリが目的のアプリ仕様内でコラボレーションのための効率的な手段を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="ba067-204">該当なし</span><span class="sxs-lookup"><span data-stu-id="ba067-204">NA</span></span> | <span data-ttu-id="ba067-205">サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。</span><span class="sxs-lookup"><span data-stu-id="ba067-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="ba067-206">精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-207">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-207">How to measure</span></span>

* <span data-ttu-id="ba067-208">空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="ba067-209">正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。</span><span class="sxs-lookup"><span data-stu-id="ba067-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-210">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-210">Recommendations</span></span>

* <span data-ttu-id="ba067-211">空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="ba067-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="ba067-212">最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba067-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="ba067-213">特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ba067-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="ba067-214">不適切に設定した interpupilary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="ba067-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="ba067-215">常に HoloLens をユーザーの IPD に構成します。</span><span class="sxs-lookup"><span data-stu-id="ba067-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-216">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-217">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-217">Documentation</span></span>

* [<span data-ttu-id="ba067-218">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="ba067-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="ba067-219">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="ba067-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="ba067-220">空間アンカーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="ba067-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="ba067-221">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="ba067-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="ba067-222">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="ba067-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="ba067-223">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="ba067-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-224">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-224">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-225">MR 空間 230: 空間マッピング</span><span class="sxs-lookup"><span data-stu-id="ba067-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ba067-226">MR ツールキット, 空間マッピングライブラリ</span><span class="sxs-lookup"><span data-stu-id="ba067-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="ba067-227">MR コンパニオンキット、ポスター調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="ba067-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="ba067-228">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="ba067-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="ba067-229">外部参照</span><span class="sxs-lookup"><span data-stu-id="ba067-229">External references</span></span>

* [<span data-ttu-id="ba067-230">Lowes のケーススタディ、有効桁数のアラインメント</span><span class="sxs-lookup"><span data-stu-id="ba067-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="ba067-231">快適なゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="ba067-231">Viewing zone of comfort</span></span>

<span data-ttu-id="ba067-232">アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="ba067-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="ba067-233">Hololens のディスプレイは、ユーザーから約2.0 分離れた光学距離で固定されているため、HoloLens を装着したユーザーは常に 2.0 m に対応して明確なイメージを維持します。</span><span class="sxs-lookup"><span data-stu-id="ba067-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="ba067-234">不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-235">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-237"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-238">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-239">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="ba067-240">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="ba067-241">コンテンツを2m に配置します。</span><span class="sxs-lookup"><span data-stu-id="ba067-241">Place content at 2m.</span></span></li><li><span data-ttu-id="ba067-242">ホログラムを2m に配置できず、収束と設備の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m と5分の間になります。</span><span class="sxs-lookup"><span data-stu-id="ba067-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="ba067-243">どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</span><span class="sxs-lookup"><span data-stu-id="ba067-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="ba067-244">シナリオで特に要求されていない限り、クリッププレーンは1m から始まる fadeout で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="ba067-245">Motionless ホログラムの詳細な監視が必要な場合は、コンテンツを50cm より近くにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba067-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="ba067-246">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-246">Meets</span></span></td><td> <span data-ttu-id="ba067-247">コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ba067-248">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-248">Fail</span></span> </td><td> <span data-ttu-id="ba067-249">コンテンツがあまりに表示されない (通常は 1.25 m &lt;、またはより詳細な監視を必要とする静止したホログラムの場合は 50cm &lt;ます)。</span><span class="sxs-lookup"><span data-stu-id="ba067-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="ba067-250">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-250">How to measure</span></span>

* <span data-ttu-id="ba067-251">通常、コンテンツは2m である必要がありますが、1.25 以上、5分を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba067-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="ba067-252">例外がいくつかある場合は、1 m から開始したコンテンツの fadeout を使用して、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="ba067-253">コンテンツにアプローチし、クリッピング平面効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="ba067-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="ba067-254">静止コンテンツは、50cm を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba067-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-255">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-255">Recommendations</span></span>

* <span data-ttu-id="ba067-256">最適な表示距離が2m のコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="ba067-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="ba067-257">1m からのコンテンツの fadeout を使用して、クリッピングレンダリング距離を85cm に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba067-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="ba067-258">近くに表示する必要がある固定のホログラムの場合、クリッピングプレーンは30cm 以下で、fadeout はクリッピング平面から少なくとも10cm 離れた位置にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-259">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-259">Resources</span></span>

* [<span data-ttu-id="ba067-260">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="ba067-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="ba067-261">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="ba067-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="ba067-262">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="ba067-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="ba067-263">テキスト、推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="ba067-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="ba067-264">深度の切り替え</span><span class="sxs-lookup"><span data-stu-id="ba067-264">Depth switching</span></span>

<span data-ttu-id="ba067-265">快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-266">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-268"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-269">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-269">✔️</span></span></td>
        <td><span data-ttu-id="ba067-270">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-271">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-271">Quality criteria</span></span>

|  <span data-ttu-id="ba067-272">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-272">Best</span></span>  |  <span data-ttu-id="ba067-273">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-273">Meets</span></span> |  <span data-ttu-id="ba067-274">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-275">ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="ba067-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="ba067-276">[突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。</span><span class="sxs-lookup"><span data-stu-id="ba067-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="ba067-277">一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="ba067-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-278">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-278">How to measure</span></span>

* <span data-ttu-id="ba067-279">アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-280">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-280">Recommendations</span></span>

* <span data-ttu-id="ba067-281">一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba067-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="ba067-282">これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-283">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-283">Resources</span></span>

* [<span data-ttu-id="ba067-284">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="ba067-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="ba067-285">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="ba067-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="ba067-286">空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="ba067-286">Use of spatial sound</span></span>

<span data-ttu-id="ba067-287">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="ba067-288">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) でサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="ba067-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="ba067-289">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="ba067-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="ba067-290">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="ba067-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-291">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-293"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-294">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-294">✔️</span></span></td>
        <td><span data-ttu-id="ba067-295">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-296">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-296">Quality criteria</span></span>

|  <span data-ttu-id="ba067-297">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-297">Best</span></span>  |  <span data-ttu-id="ba067-298">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-298">Meets</span></span> |  <span data-ttu-id="ba067-299">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-300">サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。</span><span class="sxs-lookup"><span data-stu-id="ba067-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="ba067-301">サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="ba067-302">空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。</span><span class="sxs-lookup"><span data-stu-id="ba067-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="ba067-303">サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="ba067-304">または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="ba067-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-305">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-305">How to measure</span></span>

* <span data-ttu-id="ba067-306">一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。</span><span class="sxs-lookup"><span data-stu-id="ba067-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="ba067-307">サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-308">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-308">Recommendations</span></span>

* <span data-ttu-id="ba067-309">オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="ba067-310">実際のサウンドは、合成や不自然な音よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="ba067-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="ba067-311">ほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="ba067-312">非表示の発信器は避けてください。</span><span class="sxs-lookup"><span data-stu-id="ba067-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="ba067-313">空間マスクは避けてください。</span><span class="sxs-lookup"><span data-stu-id="ba067-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="ba067-314">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="ba067-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-315">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-316">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-316">Documentation</span></span>

* [<span data-ttu-id="ba067-317">立体音響</span><span class="sxs-lookup"><span data-stu-id="ba067-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="ba067-318">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="ba067-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="ba067-319">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="ba067-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="ba067-320">ケーススタディ、HoloTour の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="ba067-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="ba067-321">RoboRaid の空間サウンドを使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="ba067-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-322">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-322">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-323">MR 空間 220: 空間サウンド</span><span class="sxs-lookup"><span data-stu-id="ba067-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="ba067-324">MRToolkit、空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="ba067-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="ba067-325">Holographic frame (視界) の境界にフォーカス</span><span class="sxs-lookup"><span data-stu-id="ba067-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="ba067-326">適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。</span><span class="sxs-lookup"><span data-stu-id="ba067-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="ba067-327">視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="ba067-328">そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="ba067-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-329">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-331"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-332">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-333">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-333">Quality criteria</span></span>

|  <span data-ttu-id="ba067-334">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-334">Best</span></span>  |  <span data-ttu-id="ba067-335">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-335">Meets</span></span> |  <span data-ttu-id="ba067-336">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-337">ユーザーはコンテキストを失うことはなく、表示も快適です。</span><span class="sxs-lookup"><span data-stu-id="ba067-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="ba067-338">ラージオブジェクトのコンテキストに関するサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="ba067-339">フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="ba067-340">一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。</span><span class="sxs-lookup"><span data-stu-id="ba067-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="ba067-341">ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="ba067-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="ba067-342">限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="ba067-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="ba067-343">ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="ba067-344">大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="ba067-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-345">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-345">How to measure</span></span>

* <span data-ttu-id="ba067-346">境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。</span><span class="sxs-lookup"><span data-stu-id="ba067-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="ba067-347">ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。</span><span class="sxs-lookup"><span data-stu-id="ba067-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="ba067-348">シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。</span><span class="sxs-lookup"><span data-stu-id="ba067-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-349">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-349">Recommendations</span></span>

* <span data-ttu-id="ba067-350">視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。</span><span class="sxs-lookup"><span data-stu-id="ba067-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="ba067-351">空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ba067-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="ba067-352">可能な限り、視界を垂直方向にクリップするホログラムは避けてください。</span><span class="sxs-lookup"><span data-stu-id="ba067-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="ba067-353">ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba067-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-354">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-355">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-355">Documentation</span></span>

* [<span data-ttu-id="ba067-356">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="ba067-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="ba067-357">ケーススタディ、HoloStudio UI、相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="ba067-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="ba067-358">オブジェクトと環境のスケール</span><span class="sxs-lookup"><span data-stu-id="ba067-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="ba067-359">カーソル、ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="ba067-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="ba067-360">外部参照</span><span class="sxs-lookup"><span data-stu-id="ba067-360">External references</span></span>

* [<span data-ttu-id="ba067-361">視界に関する多くの ado</span><span class="sxs-lookup"><span data-stu-id="ba067-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="ba067-362">ユーザーの位置に反応するコンテンツ</span><span class="sxs-lookup"><span data-stu-id="ba067-362">Content reacts to user position</span></span>

<span data-ttu-id="ba067-363">ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="ba067-364">注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。</span><span class="sxs-lookup"><span data-stu-id="ba067-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="ba067-365">ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ba067-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-366">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-368"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-369">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-369">✔️</span></span></td>
        <td><span data-ttu-id="ba067-370">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-371">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="ba067-372">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-372">Best</span></span> </td><td> <span data-ttu-id="ba067-373">コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</span><span class="sxs-lookup"><span data-stu-id="ba067-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ba067-374">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-374">Meets</span></span> </td><td> <span data-ttu-id="ba067-375">UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ba067-376">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="ba067-377">UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</span><span class="sxs-lookup"><span data-stu-id="ba067-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="ba067-378">UI 要素は、プライマリコンテンツのビューを制限します。</span><span class="sxs-lookup"><span data-stu-id="ba067-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="ba067-379">UI の移動は、特に<a href="billboarding-and-tag-along.md">タグに沿っ</a>た ui 要素によって、距離や勢いを表示するために最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="ba067-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="ba067-380">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-380">How to measure</span></span>

* <span data-ttu-id="ba067-381">すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="ba067-382">ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="ba067-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="ba067-383">UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="ba067-384">たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-385">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-385">Recommendations</span></span>

* <span data-ttu-id="ba067-386">ユーザーはカメラで、動きを制御します。</span><span class="sxs-lookup"><span data-stu-id="ba067-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="ba067-387">これらのドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-387">Let them drive.</span></span>
* <span data-ttu-id="ba067-388">テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="ba067-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="ba067-389">ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-390">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-391">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-391">Documentation</span></span>

* [<span data-ttu-id="ba067-392">相互作用の設計</span><span class="sxs-lookup"><span data-stu-id="ba067-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="ba067-393">色、光、素材</span><span class="sxs-lookup"><span data-stu-id="ba067-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="ba067-394">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="ba067-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ba067-395">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="ba067-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ba067-396">自己動きとユーザー locomotion</span><span class="sxs-lookup"><span data-stu-id="ba067-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-397">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-397">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-398">MR 入力 210: 宝石</span><span class="sxs-lookup"><span data-stu-id="ba067-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="ba067-399">入力の相互作用のわかりやすさ</span><span class="sxs-lookup"><span data-stu-id="ba067-399">Input interaction clarity</span></span>

<span data-ttu-id="ba067-400">入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ba067-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="ba067-401">ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="ba067-402">アプリにカスタム入力がある場合は、それを明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="ba067-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-403">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-405"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-406">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-406">✔️</span></span></td>
        <td><span data-ttu-id="ba067-407">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-408">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-408">Quality criteria</span></span>

|  <span data-ttu-id="ba067-409">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-409">Best</span></span>  |  <span data-ttu-id="ba067-410">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-410">Meets</span></span> |  <span data-ttu-id="ba067-411">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-412">入力の相互作用メソッドは、Windows Mixed Reality に用意されている[ガイダンス](interaction-fundamentals.md)と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="ba067-413">任意のカスタム入力を標準入力で冗長にする (標準の対話を使用する) ことはできません。また、ユーザーに明確に通知してデモンストレーションする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="ba067-414">"最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。</span><span class="sxs-lookup"><span data-stu-id="ba067-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="ba067-415">ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。</span><span class="sxs-lookup"><span data-stu-id="ba067-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="ba067-416">入力方法またはボタンのマッピングを理解するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="ba067-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="ba067-417">入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-418">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-418">How to measure</span></span>

* <span data-ttu-id="ba067-419">アプリでは、一貫[した標準の入力方法が使用されます。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="ba067-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="ba067-420">アプリになる入力がある場合は、次の方法で明確に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="ba067-421">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="ba067-421">First-run experience</span></span>
* <span data-ttu-id="ba067-422">入門画面</span><span class="sxs-lookup"><span data-stu-id="ba067-422">Introductory screens</span></span>
* <span data-ttu-id="ba067-423">ヒント</span><span class="sxs-lookup"><span data-stu-id="ba067-423">Tooltips</span></span>
* <span data-ttu-id="ba067-424">手コーチ</span><span class="sxs-lookup"><span data-stu-id="ba067-424">Hand coach</span></span>
* <span data-ttu-id="ba067-425">ヘルプセクション</span><span class="sxs-lookup"><span data-stu-id="ba067-425">Help section</span></span>
* <span data-ttu-id="ba067-426">ボイスオーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-427">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-427">Recommendations</span></span>

* <span data-ttu-id="ba067-428">可能な場合は常に標準の入力方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="ba067-429">標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="ba067-430">アプリ全体で一貫した相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-431">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-432">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-432">Documentation</span></span>

* [<span data-ttu-id="ba067-433">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="ba067-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ba067-434">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ba067-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="ba067-435">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="ba067-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ba067-436">カーソル</span><span class="sxs-lookup"><span data-stu-id="ba067-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ba067-437">快適で見つめ</span><span class="sxs-lookup"><span data-stu-id="ba067-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="ba067-438">音声入力</span><span class="sxs-lookup"><span data-stu-id="ba067-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="ba067-439">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="ba067-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="ba067-440">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="ba067-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="ba067-441">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="ba067-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="ba067-442">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="ba067-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="ba067-443">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="ba067-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="ba067-444">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="ba067-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="ba067-445">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="ba067-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="ba067-446">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="ba067-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="ba067-447">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="ba067-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="ba067-448">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="ba067-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-449">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-449">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-450">ケーススタディ: よりパーソナルコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="ba067-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="ba067-451">キャストスタディ: HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="ba067-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="ba067-452">サンプルアプリ: 要素の周期テーブル</span><span class="sxs-lookup"><span data-stu-id="ba067-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="ba067-453">サンプルアプリ: 旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="ba067-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="ba067-454">MR 入力 210: 宝石</span><span class="sxs-lookup"><span data-stu-id="ba067-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="ba067-455">MR 入力 211: ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="ba067-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="ba067-456">MR 入力 212: 音声</span><span class="sxs-lookup"><span data-stu-id="ba067-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="ba067-457">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ba067-457">Interactable objects</span></span>

<span data-ttu-id="ba067-458">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="ba067-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="ba067-459">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="ba067-460">イベントをトリガーする対話型オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba067-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="ba067-461">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="ba067-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="ba067-462">フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-463">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-465"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-466">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-466">✔️</span></span></td>
        <td><span data-ttu-id="ba067-467">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-468">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-468">Quality criteria</span></span>

|  <span data-ttu-id="ba067-469">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-469">Best</span></span>  |  <span data-ttu-id="ba067-470">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-470">Meets</span></span> |  <span data-ttu-id="ba067-471">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-472">フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="ba067-473">"ご覧のように、エクスペリエンス全体で一貫して使用されています。</span><span class="sxs-lookup"><span data-stu-id="ba067-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="ba067-474">オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="ba067-475">ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="ba067-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="ba067-476">ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="ba067-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="ba067-477">オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ba067-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-478">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-478">How to measure</span></span>

* <span data-ttu-id="ba067-479">対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。</span><span class="sxs-lookup"><span data-stu-id="ba067-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="ba067-480">経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。</span><span class="sxs-lookup"><span data-stu-id="ba067-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-481">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-481">Recommendations</span></span>

* <span data-ttu-id="ba067-482">対話のためにビジュアルとオーディオフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="ba067-483">視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります</span><span class="sxs-lookup"><span data-stu-id="ba067-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="ba067-484">対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="ba067-485">グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="ba067-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="ba067-486">音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。</span><span class="sxs-lookup"><span data-stu-id="ba067-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-487">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-488">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-488">Documentation</span></span>

* [<span data-ttu-id="ba067-489">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="ba067-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ba067-490">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="ba067-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="ba067-491">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="ba067-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ba067-492">音声入力</span><span class="sxs-lookup"><span data-stu-id="ba067-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-493">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-493">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-494">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="ba067-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="ba067-495">部屋のスキャン</span><span class="sxs-lookup"><span data-stu-id="ba067-495">Room scanning</span></span>

<span data-ttu-id="ba067-496">空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="ba067-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="ba067-497">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ba067-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="ba067-498">多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="ba067-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="ba067-499">ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-500">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-502"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-503">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-504">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-504">Quality criteria</span></span>

|  <span data-ttu-id="ba067-505">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-505">Best</span></span>  |  <span data-ttu-id="ba067-506">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-506">Meets</span></span> |  <span data-ttu-id="ba067-507">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-508">ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。</span><span class="sxs-lookup"><span data-stu-id="ba067-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="ba067-509">ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。</span><span class="sxs-lookup"><span data-stu-id="ba067-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="ba067-510">空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="ba067-511">メッシュの視覚化がありません。</span><span class="sxs-lookup"><span data-stu-id="ba067-511">No visualization of mesh.</span></span> <span data-ttu-id="ba067-512">検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。</span><span class="sxs-lookup"><span data-stu-id="ba067-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ba067-513">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-513">How to measure</span></span>

* <span data-ttu-id="ba067-514">必要なルームスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ba067-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-515">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-515">Recommendations</span></span>

* <span data-ttu-id="ba067-516">ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ba067-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="ba067-517">スキャンが開始され、進行状況インジケーターなどの停止時に通信します。</span><span class="sxs-lookup"><span data-stu-id="ba067-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="ba067-518">スキャン中にメッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba067-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="ba067-519">ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="ba067-520">データを改善するための場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ba067-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="ba067-521">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-522">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="ba067-523">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ba067-523">Documentation</span></span>

* [<span data-ttu-id="ba067-524">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="ba067-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="ba067-525">ケーススタディ: HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="ba067-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="ba067-526">ケーススタディ: HoloTour の空間サウンド設計</span><span class="sxs-lookup"><span data-stu-id="ba067-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="ba067-527">ケーススタディ: フラグメントでのイマーシブエクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="ba067-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="ba067-528">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ba067-528">Tools and tutorials</span></span>

* [<span data-ttu-id="ba067-529">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="ba067-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="ba067-530">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="ba067-530">Directional indicators</span></span>

<span data-ttu-id="ba067-531">Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba067-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="ba067-532">適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。</span><span class="sxs-lookup"><span data-stu-id="ba067-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="ba067-533">ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="ba067-534">非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。</span><span class="sxs-lookup"><span data-stu-id="ba067-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-535">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-537"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-538">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-538">✔️</span></span></td>
        <td><span data-ttu-id="ba067-539">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-540">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-540">Quality criteria</span></span>

|  <span data-ttu-id="ba067-541">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-541">Best</span></span>  |  <span data-ttu-id="ba067-542">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-542">Meets</span></span> |  <span data-ttu-id="ba067-543">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-544">ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。</span><span class="sxs-lookup"><span data-stu-id="ba067-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="ba067-545">コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。</span><span class="sxs-lookup"><span data-stu-id="ba067-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="ba067-546">関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="ba067-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="ba067-547">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-547">How to measure</span></span>

* <span data-ttu-id="ba067-548">ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="ba067-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-549">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-549">Recommendations</span></span>

* <span data-ttu-id="ba067-550">関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。</span><span class="sxs-lookup"><span data-stu-id="ba067-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="ba067-551">多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ba067-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="ba067-552">方向インジケーターをカーソルに組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="ba067-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-553">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-553">Resources</span></span>

* [<span data-ttu-id="ba067-554">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="ba067-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="ba067-555">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="ba067-555">Data loading</span></span>

<span data-ttu-id="ba067-556">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="ba067-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="ba067-557">これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ba067-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="ba067-558">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="ba067-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba067-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ba067-560"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba067-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba067-561">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-561">✔️</span></span></td>
        <td><span data-ttu-id="ba067-562">✔️</span><span class="sxs-lookup"><span data-stu-id="ba067-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="ba067-563">品質基準</span><span class="sxs-lookup"><span data-stu-id="ba067-563">Quality criteria</span></span>

|  <span data-ttu-id="ba067-564">合っ</span><span class="sxs-lookup"><span data-stu-id="ba067-564">Best</span></span>  |  <span data-ttu-id="ba067-565">あっ</span><span class="sxs-lookup"><span data-stu-id="ba067-565">Meets</span></span> |  <span data-ttu-id="ba067-566">オーバー</span><span class="sxs-lookup"><span data-stu-id="ba067-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="ba067-567">データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。</span><span class="sxs-lookup"><span data-stu-id="ba067-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="ba067-568">ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="ba067-569">ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="ba067-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="ba067-570">タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。</span><span class="sxs-lookup"><span data-stu-id="ba067-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="ba067-571">測定する方法</span><span class="sxs-lookup"><span data-stu-id="ba067-571">How to measure</span></span>

* <span data-ttu-id="ba067-572">データの読み込み中に、5秒を超える空の状態がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba067-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="ba067-573">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ba067-573">Recommendations</span></span>

* <span data-ttu-id="ba067-574">ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="ba067-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="ba067-575">目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="ba067-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="ba067-576">参考資料</span><span class="sxs-lookup"><span data-stu-id="ba067-576">Resources</span></span>

* [<span data-ttu-id="ba067-577">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="ba067-577">Displaying progress</span></span>](progress.md)
