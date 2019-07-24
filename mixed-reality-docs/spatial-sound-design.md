---
title: 空間サウンドのデザイン
description: 空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、空間サウンド、デザイン、スタイル
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750306"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="8a6df-104">空間サウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="8a6df-104">Spatial sound design</span></span>

<span data-ttu-id="8a6df-105">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="8a6df-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="8a6df-106">[Marco ポーロ](https://en.wikipedia.org/wiki/Marco_Polo_(game))を聞いたことがある場合、または誰かが電話に電話をかけている場合は、既に空間サウンドの重要性について理解しています。</span><span class="sxs-lookup"><span data-stu-id="8a6df-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="8a6df-107">毎日の生活でサウンドキューを使用して、オブジェクトを検索したり、他のユーザーの注意を深めたり、環境をより深く理解したりします。</span><span class="sxs-lookup"><span data-stu-id="8a6df-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="8a6df-108">アプリのサウンドは、現実の世界での動作と同じように動作するので、より説得力が高く、仮想環境に適しています。</span><span class="sxs-lookup"><span data-stu-id="8a6df-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="8a6df-109">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8a6df-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8a6df-110"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="8a6df-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8a6df-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a6df-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8a6df-112"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="8a6df-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8a6df-113">空間サウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="8a6df-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="8a6df-114">✔️</span><span class="sxs-lookup"><span data-stu-id="8a6df-114">✔️</span></span></td>
        <td><span data-ttu-id="8a6df-115">✔️</span><span class="sxs-lookup"><span data-stu-id="8a6df-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="8a6df-116">混合環境での開発において、空間サウンドが持つ4つの重要な点</span><span class="sxs-lookup"><span data-stu-id="8a6df-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="8a6df-117">既定では、サウンドはステレオで再生されます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="8a6df-118">つまり、サウンドは空間位置なしで再生されるので、ユーザーはサウンドの発信元を認識できません。</span><span class="sxs-lookup"><span data-stu-id="8a6df-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="8a6df-119">空間サウンドは、mixed reality 開発で主に次の4つの点を持ちます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="8a6df-120">**アース**</span><span class="sxs-lookup"><span data-stu-id="8a6df-120">**Grounding**</span></span>

<span data-ttu-id="8a6df-121">サウンドを使用しない場合、仮想オブジェクトをそのままにしておくと、仮想オブジェクトが効果的に停止します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="8a6df-122">実際のオブジェクトと同じように、これらのオブジェクトが表示されない場合でもこれらのオブジェクトを聞いて、どこからでも検索できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="8a6df-123">仮想オブジェクトを実際の世界とブレンドするために視覚的に接地する必要があるのと同じように、音声でも接地する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="8a6df-124">空間サウンドは、リアルワールドオーディオ環境とデジタルオーディオ環境をシームレスに融合します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="8a6df-125">**ユーザーへの注意**</span><span class="sxs-lookup"><span data-stu-id="8a6df-125">**User attention**</span></span>

<span data-ttu-id="8a6df-126">混合環境では、ユーザーが見ている場所を推測して、世界中に何かを視覚的に表示することを期待することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a6df-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="8a6df-127">しかし、サウンドを再生しているオブジェクトが背後にある場合でも、ユーザーは常にサウンド再生を聞くことができます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="8a6df-128">人間は、サウンドによって注意を引くために使用されています。私たちは、私たちが聞いたオブジェクトに instinctually ています。</span><span class="sxs-lookup"><span data-stu-id="8a6df-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="8a6df-129">ユーザーの宝石を特定の場所に誘導する場合は、矢印を使用して視覚的にポイントするのではなく、その場所にサウンドを配置すると、非常に簡単にガイドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="8a6df-130">**Immersion**</span><span class="sxs-lookup"><span data-stu-id="8a6df-130">**Immersion**</span></span>

<span data-ttu-id="8a6df-131">オブジェクトの移動または競合がある場合は、通常、マテリアル間の相互作用を耳にします。</span><span class="sxs-lookup"><span data-stu-id="8a6df-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="8a6df-132">したがって、オブジェクトが実際の世界では同じサウンドを作成しない場合、immersion のレベルは失われます。これは、ボリュームがすべての状態にある恐ろしいムービーを見るようなものです。</span><span class="sxs-lookup"><span data-stu-id="8a6df-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="8a6df-133">実際の世界中のすべてのサウンドは、スペースの特定の地点から来ています。ヘッドを変えると、このようなサウンドが耳から来た時点で変化することがあります。この方法では、音の場所を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="8a6df-134">Spatialized サウンドは、表示される内容を超える場所の "感覚" を構成します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="8a6df-135">**相互作用の設計**</span><span class="sxs-lookup"><span data-stu-id="8a6df-135">**Interaction design**</span></span>

<span data-ttu-id="8a6df-136">従来の対話型エクスペリエンスでは、UI サウンド効果のような相互作用音は、標準の mono またはステレオで再生されます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="8a6df-137">しかし、混合現実のすべてのものが3D 空間に存在します (UI を含む)。これらのオブジェクトは、spatialized サウンドを利用することでメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="8a6df-138">現実の世界でボタンを押すと、そのボタンから聞こえる音が聞こえます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="8a6df-139">相互作用サウンドを spatializing、さらに自然で現実的なユーザーエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="8a6df-140">空間サウンドを使用する場合のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="8a6df-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="8a6df-141">**実際のサウンドは合成または不自然なサウンドよりも優れています**</span><span class="sxs-lookup"><span data-stu-id="8a6df-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="8a6df-142">ユーザーは、サウンドの種類を使い慣れているほど、より自然なものになり、環境内でより簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="8a6df-143">たとえば、人間の声は非常に一般的な種類のサウンドです。ユーザーは、部屋にいる人と同じように簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="8a6df-144">**予測勝るシミュレーション**</span><span class="sxs-lookup"><span data-stu-id="8a6df-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="8a6df-145">特定の方向から聞こえるサウンドを使用している場合は、空間キューに関係なく、その方向に注意が付きます。たとえば、ほとんどの場合、鳥は私たちの話です。</span><span class="sxs-lookup"><span data-stu-id="8a6df-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="8a6df-146">鳥の音を再生すると、その下にサウンドを配置したとしても、ユーザーが検索する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="8a6df-147">通常、これは混乱を招くことがあるため、より自然なエクスペリエンスを実現するために使用するのではなく、このような予測を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8a6df-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="8a6df-148">**ほとんどのサウンドは spatialized にする必要があります**</span><span class="sxs-lookup"><span data-stu-id="8a6df-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="8a6df-149">前述のように、混合現実のすべてが3D 空間に存在します。サウンドも同様です。</span><span class="sxs-lookup"><span data-stu-id="8a6df-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="8a6df-150">音楽でも、特にメニューやその他の UI に関連付けられている場合は、spatialization のメリットが得られることがあります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="8a6df-151">**非表示の発信器を避ける**</span><span class="sxs-lookup"><span data-stu-id="8a6df-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="8a6df-152">私たちが耳にしたサウンドを確認するように条件が設定されているので、不自然で unnerving 経験があり、ビジュアルが存在しないサウンドを見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="8a6df-153">現実の世界におけるサウンドは、空の領域からのものではないため、オーディオエミッタがユーザーの直接の環境内に配置されている場合は、そのことも確認してください。</span><span class="sxs-lookup"><span data-stu-id="8a6df-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="8a6df-154">**空間マスクを避ける**</span><span class="sxs-lookup"><span data-stu-id="8a6df-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="8a6df-155">空間サウンドは、他のサウンドによってオーバーパワーを受ける非常に微妙な音響キューに依存します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="8a6df-156">ステレオ音楽またはアンビエントサウンドを使用している場合は、ユーザーが簡単に見つけられるようにするための spatialized サウンドの詳細を確保するために、ミックスに十分な容量があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8a6df-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="8a6df-157">空間サウンドを使用する場合に留意すべき一般的な概念</span><span class="sxs-lookup"><span data-stu-id="8a6df-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="8a6df-158">**空間サウンドはシミュレーションです**</span><span class="sxs-lookup"><span data-stu-id="8a6df-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="8a6df-159">空間サウンドを最も頻繁に使用するのは、世界中の実際のオブジェクトまたは仮想オブジェクトから emanating されているかのように聞こえます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="8a6df-160">そのため、spatialized サウンドは、このようなオブジェクトから最も意味があるものである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="8a6df-161">空間サウンドの精度が認識されていることは、オブジェクトのサイズとユーザーからの距離によっては、音が必ずしもオブジェクトの中心から出力されるとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a6df-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="8a6df-162">小さいオブジェクトでは、通常、オブジェクトの中心点で十分です。</span><span class="sxs-lookup"><span data-stu-id="8a6df-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="8a6df-163">大きなオブジェクトの場合は、サウンドを生成するオブジェクト内の特定の位置にサウンドエミッタまたは複数の発信器が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="8a6df-164">**すべてのサウンドを正規化する**</span><span class="sxs-lookup"><span data-stu-id="8a6df-164">**Normalize all sounds**</span></span>

<span data-ttu-id="8a6df-165">距離の減衰は、現実の世界でのように、ユーザーからの最初のメーター内ですばやく発生します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="8a6df-166">すべてのオーディオファイルは、物理的に正確な距離の減衰を保証し、いくつかのメーター (該当する場合) が出たときに音が聞こえるようにするために、正規化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="8a6df-167">空間オーディオエンジンは、一定の距離 (減衰と "距離の合図" を組み合わせたもの) にあるようにサウンドが "感覚" になるまでの減衰を処理し、その上に減衰を適用すると、効果が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="8a6df-168">実際のオブジェクトをシミュレートするのではなく、*空間サウンド*サウンドの初期距離の減衰が、オーディオの適切な組み合わせに対して十分ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="8a6df-169">**オブジェクト検出とユーザーインターフェイス**</span><span class="sxs-lookup"><span data-stu-id="8a6df-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="8a6df-170">オーディオキューを使用して、現在のビューを超えてユーザーの注意を促した場合、サウンドは、ステレオサウンドの上にある音で目立つようにする必要があります。また、その他の spatialized 音は、指向性オーディオキューからは聞こえない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="8a6df-171">ユーザーインターフェイスの要素 (メニューなど) に関連付けられているサウンドや音楽の場合は、サウンドエミッタをそのオブジェクトに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="8a6df-172">ステレオおよびその他の非位置オーディオ再生によって、ユーザーが spatialized の要素を見つけることが困難になる場合があります (上記を参照)。空間マスキングは避けてください。)</span><span class="sxs-lookup"><span data-stu-id="8a6df-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="8a6df-173">**可能な限り標準3D サウンドに対する空間サウンドを使用する**</span><span class="sxs-lookup"><span data-stu-id="8a6df-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="8a6df-174">混合現実では、最適なユーザーエクスペリエンスを実現するために、従来の3D オーディオテクノロジではなく、空間サウンドを使用して3D オーディオを実現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a6df-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="8a6df-175">一般に、改善された spatialization は、標準3D サウンドよりも小さい CPU コストに相当します。</span><span class="sxs-lookup"><span data-stu-id="8a6df-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="8a6df-176">標準3D オーディオは、優先度の低いサウンド、spatialized されているが物理オブジェクトまたは仮想オブジェクトに関連付けられていないサウンド、およびユーザーがアプリケーションと対話するために必要としないオブジェクトを検索するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a6df-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a6df-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a6df-177">See also</span></span>
* [<span data-ttu-id="8a6df-178">立体音響</span><span class="sxs-lookup"><span data-stu-id="8a6df-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="8a6df-179">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="8a6df-179">Spatial mapping</span></span>](spatial-mapping.md)
