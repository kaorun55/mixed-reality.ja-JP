---
title: 立体音響
description: 混合 reality アプリケーションで空間サウンドを使用すると、3D 空間にサウンドを convincingly ことができます。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空間サウンド、サラウンドサウンド、3d オーディオ、3d サウンド、空間オーディオ
ms.openlocfilehash: 31ec8f88a060127daab9bf3afc970457ec7c90a3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437393"
---
# <a name="spatial-sound"></a><span data-ttu-id="7963a-104">立体音響</span><span class="sxs-lookup"><span data-stu-id="7963a-104">Spatial sound</span></span>

<span data-ttu-id="7963a-105">オブジェクトが目に見えなくなったときに、私たちが何をしているのかを確認する方法の1つは、サウンドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="7963a-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="7963a-106">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、mixed reality の aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="7963a-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="7963a-107">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) でサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="7963a-108">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="7963a-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="7963a-109">[ホログラム](hologram.md)が光の付いたオブジェクトであり、音がかかることがあるので、サウンドコンポーネントは、believable を増やし、よりイマーシブなエクスペリエンスを作成するために、地面のホログラムに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7963a-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="7963a-110">ホログラムは、ユーザーの宝石が指している場所でのみ視覚的に表示できますが、アプリのサウンドはすべての方向から取得できます。上、下、背後、その他この機能を使用すると、現在ユーザーの表示に含まれていない可能性があるオブジェクトに注意を促すことができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="7963a-111">ユーザーは、混合現実の世界でソースから emanating されるような音を感じることができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="7963a-112">たとえば、ユーザーがオブジェクトに近づいたり、オブジェクトに近づいたりすると、ボリュームが増加します。</span><span class="sxs-lookup"><span data-stu-id="7963a-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="7963a-113">同様に、オブジェクトがユーザーの周りを移動する場合や、その逆の場合は、空間サウンドによって、サウンドがオブジェクトから直接送られるようになります。</span><span class="sxs-lookup"><span data-stu-id="7963a-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="7963a-114">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="7963a-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7963a-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="7963a-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7963a-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7963a-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7963a-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7963a-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7963a-118"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="7963a-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7963a-119">立体音響</span><span class="sxs-lookup"><span data-stu-id="7963a-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="7963a-120">✔️</span><span class="sxs-lookup"><span data-stu-id="7963a-120">✔️</span></span></td>
        <td><span data-ttu-id="7963a-121">✔️</span><span class="sxs-lookup"><span data-stu-id="7963a-121">✔️</span></span></td>
        <td><span data-ttu-id="7963a-122">✔️ (ヘッドフォンあり)</span><span class="sxs-lookup"><span data-stu-id="7963a-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="7963a-123">認識された場所とサウンドの距離をシミュレートする</span><span class="sxs-lookup"><span data-stu-id="7963a-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="7963a-124">サウンドが耳の両方に到達したかを分析することで、脳は、サウンドを生成するオブジェクトの距離と方向を決定します。</span><span class="sxs-lookup"><span data-stu-id="7963a-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="7963a-125">HRTF (または Head 関連の転送関数) は、ポイントの地点からの耳の反応を特徴付けるスペクトル応答をモデル化することで、この相互作用をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="7963a-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="7963a-126">空間オーディオエンジンでは、カスタマイズされた HRTFs を使用して、mixed reality エクスペリエンスを拡張し、さまざまな方向や距離からのサウンドをシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="7963a-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="7963a-127">左または右のオーディオ (azimuth) のキューは、各 ear でサウンドが到着したときの違いに起因します。</span><span class="sxs-lookup"><span data-stu-id="7963a-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="7963a-128">上下のキューは、外側の ear 図形 (pinnae) によって生成されたスペクトル変化から発生します。</span><span class="sxs-lookup"><span data-stu-id="7963a-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="7963a-129">オーディオの発信元を指定することにより、システムは、耳に異なる時刻に到着したサウンドのエクスペリエンスをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="7963a-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="7963a-130">HoloLens では、azimuth spatialization はパーソナル化されていますが、昇格のシミュレーションは平均 anthropometrics のセットに基づいていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7963a-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="7963a-131">したがって、昇格の精度は azimuth の精度よりも正確ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7963a-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="7963a-132">サウンドの特性は、それらが存在する環境によっても変わります。</span><span class="sxs-lookup"><span data-stu-id="7963a-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="7963a-133">たとえば、岩穴で叫んを使用すると、音声が壁、床、および雲に出、エコー効果が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7963a-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="7963a-134">空間サウンドの部屋モデル設定は、特定のオーディオ環境でサウンドを配置するために、これらの反射を再現します。</span><span class="sxs-lookup"><span data-stu-id="7963a-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="7963a-135">この設定を使用すると、ユーザーの実際の場所を一致させて、よりイマーシブなオーディオエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="7963a-136">空間サウンドの統合</span><span class="sxs-lookup"><span data-stu-id="7963a-136">Integrating spatial sound</span></span>

<span data-ttu-id="7963a-137">混合現実の一般的な原則は、ユーザーの物理的な世界または仮想環境での最先端の[ホログラム](hologram.md)であるため、ホログラムからのほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7963a-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="7963a-138">HoloLens では、自然に CPU とメモリの予算に関する考慮事項がありますが、CPU の使用率が12% 未満 (4 つのコアのうちの 70%) を使用して、10-12 の空間サウンド音声を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7963a-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="7963a-139">空間サウンドの音声の推奨される用途は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7963a-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="7963a-140">(特にビュー外の) オブジェクトを見つめています。</span><span class="sxs-lookup"><span data-stu-id="7963a-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="7963a-141">ホログラムにユーザーの注意が必要な場合は、そのホログラムでサウンドを再生します (例: 仮想 dog ほえ)。</span><span class="sxs-lookup"><span data-stu-id="7963a-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="7963a-142">これにより、ユーザーは、表示されていないホログラムを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="7963a-143">Audio Haptics (touchless 相互作用のためのリアクティブオーディオ)。</span><span class="sxs-lookup"><span data-stu-id="7963a-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="7963a-144">たとえば、ユーザーの手や運動コントローラーがジェスチャフレームを入力して終了したときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="7963a-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="7963a-145">または、ユーザーがホログラムを選択したときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="7963a-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="7963a-146">Immersion (ユーザーを囲むアンビエントサウンド)。</span><span class="sxs-lookup"><span data-stu-id="7963a-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="7963a-147">また、標準のステレオサウンドと空間サウンドをブレンドすると、現実的な環境を作成するのに効果的な場合があることに注意してください。ステレオサウンドは、反射 (距離の手掛かり) は、ノイズの多い環境では聞こえにくいことがあります。</span><span class="sxs-lookup"><span data-stu-id="7963a-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="7963a-148">Windows の空間サウンドエンジンでは、再生用に 48 k サンプルレートのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7963a-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="7963a-149">Unity などのほとんどのミドルウェアでは、サウンドファイルはサポートされている形式に自動的に変換されますが、Windows Audio Api を直接使用する場合は、コンテンツの形式を、その効果でサポートされている形式に一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="7963a-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="7963a-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="7963a-150">See also</span></span>
* [<span data-ttu-id="7963a-151">MR 空間220</span><span class="sxs-lookup"><span data-stu-id="7963a-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="7963a-152">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="7963a-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="7963a-153">DirectX の立体音響</span><span class="sxs-lookup"><span data-stu-id="7963a-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="7963a-154">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="7963a-154">Spatial sound design</span></span>](spatial-sound-design.md)
