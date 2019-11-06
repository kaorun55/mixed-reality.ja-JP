---
title: 混合現実のオーディオ
description: 混合現実のオーディオを使用すると、UI インタラクションのユーザーの信頼を高め、ユーザーのエクスペリエンスをこちらことができます。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間サウンド、サラウンドサウンド、3d オーディオ、3d サウンド、空間オーディオ
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641115"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="a616e-104">混合現実のオーディオ</span><span class="sxs-lookup"><span data-stu-id="a616e-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="a616e-105">オーディオは、混合現実の設計と生産性の重要な部分であり、次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="a616e-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="a616e-106">ジェスチャと音声ベースの対話でユーザーの信頼度を高める</span><span class="sxs-lookup"><span data-stu-id="a616e-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="a616e-107">ユーザーガイドの次の手順</span><span class="sxs-lookup"><span data-stu-id="a616e-107">Guide users to next steps</span></span>
* <span data-ttu-id="a616e-108">仮想オブジェクトを実際の世界と効果的に組み合わせる</span><span class="sxs-lookup"><span data-stu-id="a616e-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="a616e-109">HoloLens を含む mixed reality ヘッドセットの待機時間の短いヘッドトラッキングでは、高品質の HRTF ベースの spatialization を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a616e-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="a616e-110">アプリケーションの Spatializing オーディオは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a616e-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="a616e-111">ビジュアル要素へのアテンション呼び出し</span><span class="sxs-lookup"><span data-stu-id="a616e-111">Call attention to visual elements</span></span>
* <span data-ttu-id="a616e-112">ユーザーが実際の環境を認識できるようにする</span><span class="sxs-lookup"><span data-stu-id="a616e-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="a616e-113">Acoustics を追加すると、ホログラムが混合世界に接続され、環境とオブジェクトの状態に関する手掛かりを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="a616e-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="a616e-114">オーディオを使用したデザインの詳細な例については、「[サウンドのデザイン](spatial-sound-design.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a616e-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="a616e-115">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="a616e-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a616e-116"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="a616e-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a616e-117"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a616e-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a616e-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a616e-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a616e-119"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="a616e-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a616e-120">Spatialization</span><span class="sxs-lookup"><span data-stu-id="a616e-120">Spatialization</span></span></td>
        <td><span data-ttu-id="a616e-121">✔️</span><span class="sxs-lookup"><span data-stu-id="a616e-121">✔️</span></span></td>
        <td><span data-ttu-id="a616e-122">✔️</span><span class="sxs-lookup"><span data-stu-id="a616e-122">✔️</span></span></td>
        <td><span data-ttu-id="a616e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a616e-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a616e-124">Spatialization ハードウェアアクセラレーション</span><span class="sxs-lookup"><span data-stu-id="a616e-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a616e-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a616e-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="a616e-126">Mixed reality でのサウンドの使用</span><span class="sxs-lookup"><span data-stu-id="a616e-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="a616e-127">[Mixed reality でサウンドを使用](spatial-sound-design.md)する場合、タッチおよびキーボードおよびマウスアプリケーションとは別のアプローチが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a616e-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="a616e-128">サウンド設計の主な決定事項には、どのようなサウンドを spatialize し、どのような対話を sonify にするかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a616e-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="a616e-129">これらの決定は、ユーザーの自信、生産性、学習曲線に大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a616e-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="a616e-130">導入事例</span><span class="sxs-lookup"><span data-stu-id="a616e-130">Case studies</span></span>
<span data-ttu-id="a616e-131">HoloTour は事実上、世界中の tourist と歴史的なサイトにユーザーを移動させることになります。</span><span class="sxs-lookup"><span data-stu-id="a616e-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="a616e-132">次のケーススタディでは、HoloTour の HoloTour: [sound design](case-study-spatial-sound-design-for-holotour.md)のサウンドデザインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a616e-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="a616e-133">特殊なマイクとレンダリングのセットアップを使用して、サブジェクトスペースがキャプチャされました。</span><span class="sxs-lookup"><span data-stu-id="a616e-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="a616e-134">RoboRaid は、HoloLens の高エネルギー shooter です。</span><span class="sxs-lookup"><span data-stu-id="a616e-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="a616e-135">次のケーススタディでは、空間オーディオを最大限に利用するために使用されたデザインの選択について説明します。 [RoboRaid のサウンドデザイン](case-study-using-spatial-sound-in-roboraid.md)です。</span><span class="sxs-lookup"><span data-stu-id="a616e-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="a616e-136">Spatialization</span><span class="sxs-lookup"><span data-stu-id="a616e-136">Spatialization</span></span>
<span data-ttu-id="a616e-137">Spatialization は、空間オーディオの方向コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a616e-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="a616e-138">7\.1 home シアターセットアップを使用する場合、spatialization は、スピーカー間のパンと同様に簡単です。</span><span class="sxs-lookup"><span data-stu-id="a616e-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="a616e-139">しかし、ヘッドホンが混在している場合は、正確さと快適さを実現するために HRTF ベースのテクノロジを使用することが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="a616e-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="a616e-140">Windows には HRTF ベースの spatialization が用意されており、このサポートは HoloLens 2 でハードウェアアクセラレータを利用しています。</span><span class="sxs-lookup"><span data-stu-id="a616e-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="a616e-141">Spatialize ですか。</span><span class="sxs-lookup"><span data-stu-id="a616e-141">Should I spatialize?</span></span>
<span data-ttu-id="a616e-142">Mixed reality アプリケーションの多くのサウンドには、リスナーの頭から音を spatialization、世界中に配置する、という利点があります。</span><span class="sxs-lookup"><span data-stu-id="a616e-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="a616e-143">アプリケーションで spatialization を最も効果的に使用するための推奨事項については、「[空間サウンドの設計](spatial-sound-design.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a616e-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="a616e-144">Spatializer のパーソナル化</span><span class="sxs-lookup"><span data-stu-id="a616e-144">Spatializer personalization</span></span>
<span data-ttu-id="a616e-145">HRTFs は、頻度の範囲内の耳間のレベルとフェーズの差を操作します。</span><span class="sxs-lookup"><span data-stu-id="a616e-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="a616e-146">これらは、物理的なモデルと、人間の頭、torso および ear 図形 (pinnae) の測定値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a616e-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="a616e-147">脳は、これらの違いに対応して、サウンドの方向を認識します。</span><span class="sxs-lookup"><span data-stu-id="a616e-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="a616e-148">各個人には、独自の ear 図形、ヘッドサイズ、および耳の位置があります。したがって、最適な HRTFs は自分に準拠しているものです。</span><span class="sxs-lookup"><span data-stu-id="a616e-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="a616e-149">HoloLens では、ヘッドセットから pupilary distance (IPD) を使用して spatialization の精度が向上し、ヘッドサイズに対して HRTFs が調整されます。</span><span class="sxs-lookup"><span data-stu-id="a616e-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="a616e-150">Spatializer プラットフォームのサポート</span><span class="sxs-lookup"><span data-stu-id="a616e-150">Spatializer platform support</span></span>
<span data-ttu-id="a616e-151">Windows では、 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)を使用して、hrtfs などの spatialization を提供しています。</span><span class="sxs-lookup"><span data-stu-id="a616e-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="a616e-152">この API は、HoloLens 2 HRTF ハードウェアアクセラレーションをアプリケーションに公開します。</span><span class="sxs-lookup"><span data-stu-id="a616e-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="a616e-153">Spatializer ミドルウェアのサポート</span><span class="sxs-lookup"><span data-stu-id="a616e-153">Spatializer middleware support</span></span>
<span data-ttu-id="a616e-154">Windows の HRTFs のサポートは、一部のサードパーティのオーディオエンジンで利用できます。</span><span class="sxs-lookup"><span data-stu-id="a616e-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="a616e-155">[Unity オーディオエンジン](spatial-sound-in-unity.md)プラグインは HRTF xapo を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a616e-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="a616e-156">[Wwise なオーディオエンジンプラグイン](https://www.audiokinetic.com/products/plug-ins/msspatial/)は、ISpatialAudioClient API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a616e-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="a616e-157">Acoustics</span><span class="sxs-lookup"><span data-stu-id="a616e-157">Acoustics</span></span>
<span data-ttu-id="a616e-158">空間オーディオは、方向よりも大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a616e-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="a616e-159">閉鎖、障害物、リバーブ、portalling、ソースモデリングなどの他のディメンションは、総称して "acoustics" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a616e-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="a616e-160">Acoustics を使用しない場合、spatialized サウンドには認識できない距離があります。</span><span class="sxs-lookup"><span data-stu-id="a616e-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="a616e-161">Acoustics の扱いは、単純なものから非常に複雑なものまでさまざまです。</span><span class="sxs-lookup"><span data-stu-id="a616e-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="a616e-162">任意のオーディオエンジンでサポートされているような単純なリバーブを使用すると、リスナーを囲む環境に spatialized サウンドをプッシュできます。</span><span class="sxs-lookup"><span data-stu-id="a616e-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="a616e-163">[プロジェクト acoustics](https://aka.ms/acoustics)などの acoustics システムから、より豊富で説得力のある acoustics 処理を利用できます。</span><span class="sxs-lookup"><span data-stu-id="a616e-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="a616e-164">Project Acoustics は、壁、ドア、およびその他のシーンジオメトリの効果をサウンドでモデル化できます。これは、開発時に関連するシーンジオメトリが既知の場合に有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="a616e-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

