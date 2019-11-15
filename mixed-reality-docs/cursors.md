---
title: カーソル
description: ターゲットベクターのカーソルまたはインジケーターは、ユーザーに対して継続的なフィードバックを提供し、HoloLens がその意図を理解しているかどうかを把握します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第1世代)、HoloLens 2、Mixed Reality、カーソル、ターゲット設定、宝石、ジェスチャ
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105743"
---
# <a name="cursors"></a><span data-ttu-id="8ca2c-104">カーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-104">Cursors</span></span>

![カーソル](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="8ca2c-106">現在のターゲットベクターのカーソルまたはインジケーターは、その時点でヘッドセットが現在のフォーカスを認識している場所を理解するための継続的なフィードバックをユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="8ca2c-107">カーソルを使用すると、ユーザーは現在のターゲットポイントを理解し、フィードバックとして機能し、どの領域、ホログラム、またはポイントが入力に応答するかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="8ca2c-108">これは、デバイスがユーザーの注意を認識している場所のデジタル表現です (ただし、意図したものを決定することと同じではない可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="8ca2c-109">カーソルによって提供されるフィードバックは、システムがどのように応答するかを予測し、その信号をフィードバックとして使用して、デバイスとの通信を強化し、最終的には相互作用に関して自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="8ca2c-110">カーソルには、**指、射線**、および**頭を見つめ**た3種類があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="8ca2c-111">これらのポイントカーソルは、HoloLens、HoloLens 2、およびイマーシブヘッドセットのさまざまな入力感覚様相で動作します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="8ca2c-112">次に、各種類のヘッドセットと相互作用モデルに使用するカーソルの種類に関するガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="8ca2c-113">Mixed Reality Toolkit (MRTK) では、右のポイントエクスペリエンスを構築するのに役立つドラッグアンドドロップカーソルモジュールを作成しました。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="8ca2c-114">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="8ca2c-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8ca2c-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="8ca2c-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8ca2c-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca2c-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8ca2c-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8ca2c-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8ca2c-118"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="8ca2c-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8ca2c-119">指カーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="8ca2c-120">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="8ca2c-121">射線カーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="8ca2c-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-122">✔️</span></span></td>
        <td><span data-ttu-id="8ca2c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="8ca2c-124">頭を見つめたカーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="8ca2c-125">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-125">✔️</span></span></td>
        <td><span data-ttu-id="8ca2c-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-126">✔️</span></span></td>
        <td><span data-ttu-id="8ca2c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8ca2c-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="8ca2c-128">指カーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-128">Finger cursor</span></span>
<span data-ttu-id="8ca2c-129">この指カーソルは HoloLens 2 でのみ利用可能で、"[直接操作による操作](direct-manipulation.md)" 対話モードを強化します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="8ca2c-130">指がどこを指しているかをより深く理解するために、両方のインデックス指のヒントにリングを添付しました。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="8ca2c-131">リングサイズは、UI 画面への指の近接部分 (指の近く、リングが小さくなります) に基づいており、指が UI に接続したときにドットの形に縮小されます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="8ca2c-132">指カーソルを ![](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="8ca2c-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="8ca2c-133">"**指カーソル 1" の視覚的なフィードバックの状態**: リングがドットに縮小されます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="8ca2c-134">2: リングは画面と一致します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="8ca2c-135">3: リングは、指ベクターに対して垂直になります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="8ca2c-136">4: リングがありません。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="8ca2c-137">射線カーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-137">Ray cursor</span></span>
<span data-ttu-id="8ca2c-138">射線のカーソルは、遠くにある光線の端に接続して、手に届かないオブジェクトを操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="8ca2c-139">イマーシブヘッドセットでは、光線がモーションコントローラーから撮影され、ドットカーソルで終了します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="8ca2c-140">HoloLens 2 では、これらの運動コントローラー光線のメンタルモデルと、直接操作で使用される指カーソルと一貫性のあるリング型のカーソルでてのひらから端が出た、設計された手書き光線を活用します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="8ca2c-141">![レイカーソルコントローラー](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="8ca2c-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="8ca2c-142">**モーションコントローラーの射線カーソル**</span><span class="sxs-lookup"><span data-stu-id="8ca2c-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8ca2c-143">![レイカーソルハンド](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="8ca2c-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="8ca2c-144">**ハンドカーソル**</span><span class="sxs-lookup"><span data-stu-id="8ca2c-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="8ca2c-145">頭を見つめたカーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-145">Head-gaze cursor</span></span>
<span data-ttu-id="8ca2c-146">ヘッドを見つめたカーソルは、先端の位置と回転を使用する、非表示のヘッドを見つめたベクターの終点に接続するドットです。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="8ca2c-147">アクションを実行するために、このポインティングカーソルは、エアタップ、音声コマンド、熟考、ボタンの押下などのさまざまなコミット入力とペアになっています。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="8ca2c-148">HoloLens 2 では、ヘッドを使用することをお勧めします。これは、エアタップ以外のすべてのコミット入力とペアになります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="8ca2c-149">![ヘッドを見つめたカーソルハンド](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="8ca2c-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="8ca2c-150">**ハンドジェスチャを使用した頭を見つめたカーソル**</span><span class="sxs-lookup"><span data-stu-id="8ca2c-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8ca2c-151">![ヘッドを見つめたカーソルの音声](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="8ca2c-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="8ca2c-152">**音声コマンドを使用した頭を見つめたカーソル**</span><span class="sxs-lookup"><span data-stu-id="8ca2c-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="8ca2c-153">カーソルのカスタマイズに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="8ca2c-153">Cursor customization recommendations</span></span>
<span data-ttu-id="8ca2c-154">カーソルフィードバックの動作と外観をカスタマイズする場合は、次のような設計上の推奨事項があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="8ca2c-155">カーソルのスケール</span><span class="sxs-lookup"><span data-stu-id="8ca2c-155">Cursor scale</span></span>
* <span data-ttu-id="8ca2c-156">カーソルは、使用可能なターゲットを超えないようにする必要があります。これにより、ユーザーは簡単に操作してコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="8ca2c-157">作成したエクスペリエンスに応じて、ユーザーが見ているようにカーソルを拡大縮小することも重要な考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="8ca2c-158">たとえば、ユーザーがさらに経験を持っているときは、カーソルが失われないように、カーソルが小さすぎないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="8ca2c-159">カーソルをスケーリングするときは、サイズを変更して自然な感覚を与えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="8ca2c-160">Obstructing コンテンツは避けてください。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-160">Avoid obstructing content.</span></span> <span data-ttu-id="8ca2c-161">ホログラムを使用すると、エクスペリエンスがわかりやすくなり、カーソルを離れることはできません。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="8ca2c-162">Directionless カーソルのシェイプ</span><span class="sxs-lookup"><span data-stu-id="8ca2c-162">Directionless cursor shape</span></span>
* <span data-ttu-id="8ca2c-163">1つの右カーソル図形はありませんが、トーラスのような directionless 図形を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="8ca2c-164">ある方向を指すカーソル (たとえば、従来の矢印カーソル) は、ユーザーが常にそのように見えるように混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="8ca2c-165">この例外は、カーソルを使用して対話命令をユーザーに伝える場合です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="8ca2c-166">たとえば、混合の現実 OS でホログラムをスケーリングする場合、カーソルには一時的に矢印が表示されます。矢印を使用すると、ハンドを移動してホログラムをスケーリングする方法をユーザーに指示することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="8ca2c-167">ルックアンドフィール</span><span class="sxs-lookup"><span data-stu-id="8ca2c-167">Look and feel</span></span>
* <span data-ttu-id="8ca2c-168">ドーナツカーソルまたはトーラスカーソルは、多数のアプリケーションで動作します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="8ca2c-169">作成するエクスペリエンスを最もよく表す色と形状を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="8ca2c-170">カーソルは、特に[色の分離](hologram-stability.md#color-separation)が非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="8ca2c-171">均衡がとれた小さいカーソルは、視覚的な階層を占めことなく、有益な情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="8ca2c-172">Cognizant を使用すると、コンテンツが妨げされたり、作業が邪魔されたりする可能性があるため、カーソルの背後に影を付けたりハイライトしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="8ca2c-173">カーソルは、アプリ内の画面に合わせて調整する必要があります。これにより、ユーザーは、システムが見ている場所を確認できるようになります。また、システムが周囲を認識していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="8ca2c-174">たとえば、Mixed Reality OS では、カーソルはユーザーの世界の表面に配置され、ユーザーがホログラムを直接見ていない場合でも、世界を認識しています。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="8ca2c-175">対話的な要素が近接している場合は、その要素にカーソルを合わせてロックすることで、ユーザーが選択操作を実行したときにその要素と対話する自信を深めることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="8ca2c-176">視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="8ca2c-176">Visual cues</span></span>
* <span data-ttu-id="8ca2c-177">1つのホログラムに焦点を絞った経験がある場合、そのホログラムから離れると、カーソルはそのホログラムと change 図形だけを hug して、変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="8ca2c-178">これは、ホログラムが実用的であり、それと対話できることをユーザーに伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="8ca2c-179">アプリケーションで空間マッピングが使用されている場合は、カーソルが表示されるすべての画面を配置し、hug することができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="8ca2c-180">これにより、HoloLens を使用するユーザーに対してフィードバックが提供され、アプリケーションはその領域を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="8ca2c-181">これにより、ホログラムは実際のものであり、現実と仮想の間のギャップを埋めることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="8ca2c-182">ビューにホログラムや surface が存在しない場合のカーソルの動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="8ca2c-183">ユーザーの前にあらかじめ定義されている距離で配置することは、1つの選択肢です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="8ca2c-184">実行可能なアクション</span><span class="sxs-lookup"><span data-stu-id="8ca2c-184">Possible actions</span></span>
* <span data-ttu-id="8ca2c-185">カーソルはさまざまなアイコンで表すことができます。これにより、ホログラムが実行できるアクション (スケーリングや回転など) を伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="8ca2c-186">カーソルがユーザーに対して何かを意味する場合にのみ、追加情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="8ca2c-187">そうしないと、ユーザーは状態の変化を気付かないか、カーソルによって混乱を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="8ca2c-188">入力状態</span><span class="sxs-lookup"><span data-stu-id="8ca2c-188">Input state</span></span>
* <span data-ttu-id="8ca2c-189">カーソルを使用して、ユーザーの入力状態または目的を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="8ca2c-190">たとえば、システムに手の状態が表示され、アプリケーションがアクションを実行する準備ができていることをユーザーに通知するアイコンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="8ca2c-191">また、カーソルを使用して、ボイスコマンドがシステムによって瞬間的に聞こえたことをユーザーに示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="8ca2c-192">次のカーソルの状態は、さまざまな方法で実装できます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="8ca2c-193">ステートマシンのようにカーソルをモデル化することによって、これらの異なる状態を実装する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="8ca2c-194">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-194">For example:</span></span>
    * <span data-ttu-id="8ca2c-195">アイドル状態は、既定のカーソルを表示する場所です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="8ca2c-196">準備完了の状態は、ユーザーの手が準備完了の位置にあることを検出したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="8ca2c-197">対話状態は、ユーザーが特定の操作を実行しているときに行われます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="8ca2c-198">考えられるアクションの状態またはホバー状態は、ホログラムで実行できるアクションを伝達するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="8ca2c-199">また、これらの状態は、さまざまな状態が検出されたときに異なるアートアセットを表示できるように、スキン対応の方法で実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="8ca2c-200">"カーソルを利用しない"</span><span class="sxs-lookup"><span data-stu-id="8ca2c-200">Going "cursor-free"</span></span>
<span data-ttu-id="8ca2c-201">Immersion の意味がエクスペリエンスの重要なコンポーネントであり、相互作用 (宝石とジェスチャを使用して) をポイントするときに、優れた精度を必要としない場合は、カーソルを使用せずにデザインすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="8ca2c-202">システムは、カーソルによって通常満たされているニーズを満たす必要があります。これは、ユーザーがポイントを理解し、システムに対する意思疎通を確実に伝えるために、システムに対する継続的なフィードバックをユーザーに提供するためです。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="8ca2c-203">これは、他の顕著な状態の変更によって実現可能です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="8ca2c-204">Unity の MRTK (Mixed Reality Toolkit) のカーソル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-204">Cursor in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="8ca2c-205">既定では、 **[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、シェルのシステムカーソルと同じビジュアル状態を持つカーソル事前 Fab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-205">By default, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="8ca2c-206">これは、MRTK の入力プロファイルの [ポインター] の下に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="8ca2c-207">このカーソルを置き換えたり、カスタマイズしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="8ca2c-208">アイトラッキング入力のエクスペリエンスを実現するために、MRTK には EyeGazeCursor が用意されており、視覚効果を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="8ca2c-209">MRTK-ポインタープロファイル</span><span class="sxs-lookup"><span data-stu-id="8ca2c-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="8ca2c-210">MRTK-入力システム</span><span class="sxs-lookup"><span data-stu-id="8ca2c-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="8ca2c-211">MRTK-ポインター</span><span class="sxs-lookup"><span data-stu-id="8ca2c-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="8ca2c-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ca2c-212">See also</span></span>
* [<span data-ttu-id="8ca2c-213">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="8ca2c-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8ca2c-214">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="8ca2c-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
