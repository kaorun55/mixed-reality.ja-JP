---
title: 目盛り
description: IPD (interpupillary distance) を調整することで、ビジュアルの品質を向上させることができます。 HoloLens および Windows Mixed Reality イマーシブヘッドセットは、IPD をカスタマイズする方法を提供します。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 調整、快適、ビジュアル、品質、ipd
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122089"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="1fc7e-105">視覚の品質と快適さを向上させる</span><span class="sxs-lookup"><span data-stu-id="1fc7e-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="1fc7e-106">HoloLens、HoloLens 2、および Windows Mixed Reality のイマーシブヘッドセットは、ビジュアルエクスペリエンスの品質を向上させるためのさまざまな方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve the quality of the visual experience.</span></span> 

## <a name="hololens-2"></a><span data-ttu-id="1fc7e-107">Hololens 2</span><span class="sxs-lookup"><span data-stu-id="1fc7e-107">Hololens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="1fc7e-108">目盛り</span><span class="sxs-lookup"><span data-stu-id="1fc7e-108">Calibration</span></span>

<span data-ttu-id="1fc7e-109">Hololens 2 は、お客様にとって最高品質の視覚画像と快適さを提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-109">Hololens 2 is designed to provide the highest quality visual imagery and comfort for our customers.</span></span> <span data-ttu-id="1fc7e-110">視線追跡テクノロジは、仮想環境の表示と操作のユーザーエクスペリエンスを向上させるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-110">Eye tracking technology is used to improve the user experience of seeing and interacting with the virtual environment.</span></span>  

<span data-ttu-id="1fc7e-111">HoloLens 2 では、デバイスのセットアップ中にビジュアルを調整するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-111">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="1fc7e-112">ユーザーは、一連のターゲットを確認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-112">Users are asked to look at a set of fixation targets.</span></span> <span data-ttu-id="1fc7e-113">これにより、デバイスは、ホログラムのレンダリングを調整して、正しく配置されたホログラム、使いやすい3D 表示エクスペリエンス、および表示品質の向上を保証できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-113">This allows the device to adjust the rendering of holograms to the user to ensure accurately positioned holograms, a comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="1fc7e-114">手動でチューニングする必要がなく、すべての調整が即座に行われます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-114">All adjustments happen on-the-fly without the need for manual tuning.</span></span> <span data-ttu-id="1fc7e-115">この視点を目印として使用することで、デバイスはすべてのユーザーに対して個別に調整され、ヘッドセットが使用されるたびに少しずつシフトされるため、視覚エフェクトが調整されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-115">By using the eyes as landmarks, the device is individually adjusted to every user, and visuals are tuned as the headset shifts slightly throughout use.</span></span> <span data-ttu-id="1fc7e-116">目の位置の追跡はシステムによって内部的に使用されます。開発者は、この機能を利用するために何もする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-116">Eye position tracking is used internally by the system and developers don’t need to do anything to leverage this capability.</span></span> <span data-ttu-id="1fc7e-117">実際、この情報は開発者には提供されていません。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-117">In fact, this information is not available to developers.</span></span>
<span data-ttu-id="1fc7e-118">視線追跡システムが開発者に提供するデータの種類の詳細については、「[目の追跡 api](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-118">Please refer to the [Eye Tracking APIs](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) to learn more about the type of data the eye tracking system provides to developers.</span></span>

<span data-ttu-id="1fc7e-119">Hololens 2 では、調整を実行することで、すべてのユーザーに対して正確な視点を追跡することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-119">On Hololens 2, performing the calibration also ensures accurate eye-gaze tracking for every user.</span></span> <span data-ttu-id="1fc7e-120">視線追跡を使用すれば、アプリケーションは、ユーザーが見ている場所をリアルタイムで追跡できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-120">Eye tracking enables applications to track where the user is looking in real time.</span></span> <span data-ttu-id="1fc7e-121">これは、開発者が利用できる主要な機能であり、新しいレベルのコンテキスト、人間による理解、holographic エクスペリエンス内でのやり取りを可能にします。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-121">This is the main capability developers can leverage to enable a whole new level of context, human understanding and interactions within the holographic experience.</span></span>  

<span data-ttu-id="1fc7e-122">調整データはデバイスにローカルに保存され、アカウント情報には関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-122">The calibration data is stored locally on the device and is not associated with any account information.</span></span> <span data-ttu-id="1fc7e-123">調整なしでデバイスを使用したユーザーの記録はありません。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-123">There is no record of who has used the device without calibration.</span></span> <span data-ttu-id="1fc7e-124">これは、ユーザーが初めてデバイスを使用するときに調整するように求められます。また、以前に調整が行われなかったユーザー、または調整が失敗したかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-124">This means that users will get prompted to calibrate when they use the device for the first time, as well as users who opted out of calibration previously or if the calibration was unsuccessful.</span></span> <span data-ttu-id="1fc7e-125">調整データは、[**設定** > ] [**プライバシー** > の監視] **[トラッカー]** のデバイスからいつでも削除できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-125">The calibration data can always be deleted from the device in **Settings** > **Privacy** > **Eye Tracker**.</span></span> 

### <a name="calibration-failures"></a><span data-ttu-id="1fc7e-126">調整エラー</span><span class="sxs-lookup"><span data-stu-id="1fc7e-126">Calibration failures</span></span>
<span data-ttu-id="1fc7e-127">調整はほとんどのユーザーに対して機能しますが、ユーザーが正常に調整できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-127">Calibration should work for most users, but there are cases in which the user might be unable to calibrate successfully.</span></span>  
<span data-ttu-id="1fc7e-128">調整エラーの例としては、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-128">Some examples of calibration failures are due to:</span></span>
- <span data-ttu-id="1fc7e-129">ユーザーは、調整操作中に、調整対象を気にすることはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-129">The user got distracted and didn't look at the calibration targets during the calibration experience</span></span>
- <span data-ttu-id="1fc7e-130">ダーティまたは傷のあるデバイスのバイザーまたはデバイスのバイザーが適切に配置されていない</span><span class="sxs-lookup"><span data-stu-id="1fc7e-130">Dirty or scratched device visor or device visor not positioned properly</span></span> 
- <span data-ttu-id="1fc7e-131">特定の種類のサングラスレンズとグラス (色分けされたコンタクトレンズ、一部の toric 連絡先レンズ、IR ブロックグラス、高処方箋グラス、など)</span><span class="sxs-lookup"><span data-stu-id="1fc7e-131">Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, etc.)</span></span>
- <span data-ttu-id="1fc7e-132">汚れまたは傷</span><span class="sxs-lookup"><span data-stu-id="1fc7e-132">Dirty or scratched glasses</span></span>
- <span data-ttu-id="1fc7e-133">その他の発音、一部の eyelash 拡張機能</span><span class="sxs-lookup"><span data-stu-id="1fc7e-133">More pronounced makeup, some eyelash extensions</span></span>
- <span data-ttu-id="1fc7e-134">Occlusions の視線またはデバイスのバイザー (ヘア、太眼鏡フレーム)</span><span class="sxs-lookup"><span data-stu-id="1fc7e-134">Occlusions of eye and/or device visor (hair, some thick eyeglasses frames)</span></span>
- <span data-ttu-id="1fc7e-135">アイ physiology、特定の目の状況、またはアイ・手術 (いくつかのナローアイ、ロング eyelashes、amblyopia、n agmu、LASIK またはその他の目など)</span><span class="sxs-lookup"><span data-stu-id="1fc7e-135">Eye physiology, certain eye conditions and/or eye surgery (some narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries, etc.)</span></span>

<span data-ttu-id="1fc7e-136">調整が失敗した場合は、次のいずれかの修正を試してください。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-136">If calibration is unsuccessful, try one of these fixes:</span></span> 
- <span data-ttu-id="1fc7e-137">デバイスのバイザーをクリーニングする</span><span class="sxs-lookup"><span data-stu-id="1fc7e-137">Clean your device visor</span></span>
- <span data-ttu-id="1fc7e-138">グラスをクリーニングする</span><span class="sxs-lookup"><span data-stu-id="1fc7e-138">Clean your glasses</span></span>
- <span data-ttu-id="1fc7e-139">でデバイスのバイザーをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-139">Push your device visor all the way in</span></span>
- <span data-ttu-id="1fc7e-140">センサーや目を obstructing ていないことを確認してください (例: ヘア)</span><span class="sxs-lookup"><span data-stu-id="1fc7e-140">Make sure nothing is obstructing the sensors or your eyes (e.g., hair)</span></span> 
- <span data-ttu-id="1fc7e-141">部屋に十分な光があることと、直射日光の下にないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-141">Make sure there is enough light in your room and that you are not under direct sunlight</span></span>
- <span data-ttu-id="1fc7e-142">調整中にターゲットに慎重に従うことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-142">Make sure you are carefully following the targets during calibration</span></span>

<span data-ttu-id="1fc7e-143">すべてのガイドラインに従い、調整がまだ失敗する場合は、[**設定** > ] [**システム** > の**調整**] で調整のプロンプトを無効にすることができます。 *"新しいユーザーがこの Hololens を使用する場合は、自動的にアイ調整を実行する*ように要求する" をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-143">If you followed all guidelines and the calibration is still failing, you can disable the calibration prompt in **Settings** > **System** > **Calibration**: *"When a new person uses this Hololens, automatically ask to run eye calibration"* should be turned off.</span></span> <span data-ttu-id="1fc7e-144">これにより、ホログラムレンダリング品質と不快感が悪くなる可能性があることを理解してください。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-144">Please understand that this might result in worse hologram rendering quality and discomfort.</span></span>

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="1fc7e-145">設定から調整アプリを起動しています</span><span class="sxs-lookup"><span data-stu-id="1fc7e-145">Launching the calibration app from Settings</span></span>
1. <span data-ttu-id="1fc7e-146">HoloLens 2 の [設定] ページにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-146">Go to the Settings page on your HoloLens 2</span></span>
    * <span data-ttu-id="1fc7e-147">[開始*ジェスチャ]* を使用して、[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を表示します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-147">Use the *"Start Gesture"* to bring up the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span> <span data-ttu-id="1fc7e-148">または、単*に [スタート画面に表示]* を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-148">Alternatively, you can also simply say *"go to start"*.</span></span>
    * <span data-ttu-id="1fc7e-149">**設定**がスタートにピン留めされていない場合は、 **[すべてのアプリ]** を選択してすべてのアプリを表示します</span><span class="sxs-lookup"><span data-stu-id="1fc7e-149">If **Settings** isn't pinned to Start, select **All Apps** to view all apps</span></span>
    * <span data-ttu-id="1fc7e-150">起動**設定**</span><span class="sxs-lookup"><span data-stu-id="1fc7e-150">Launch **Settings**</span></span>
2. <span data-ttu-id="1fc7e-151">[**システム** > **調整**の視点] に移動し、[目の調整を実行] を選択します。 > </span><span class="sxs-lookup"><span data-stu-id="1fc7e-151">Navigate to **System** > **Calibration** > **Eye Calibration** and select **Run eye calibration**</span></span>


### <a name="calibration-when-sharing-a-devicesession"></a><span data-ttu-id="1fc7e-152">デバイス/セッションを共有する場合の調整</span><span class="sxs-lookup"><span data-stu-id="1fc7e-152">Calibration when sharing a device/session</span></span>
<span data-ttu-id="1fc7e-153">Hololens 2 は、デバイスのセットアップエクスペリエンスを実行する必要がなくても、ユーザー間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-153">Hololens 2 can be shared between people without the need for each person to go through the device setup experience.</span></span>
<span data-ttu-id="1fc7e-154">Hololens 2 では、ユーザーがデバイスに新しい場合にデバイスがヘッドに配置されると、ユーザーに対して視覚エフェクトを調整するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-154">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head if the user is new to the device.</span></span> <span data-ttu-id="1fc7e-155">ユーザーがデバイスで以前にビジュアルを調整している場合は、ユーザーがデバイスをヘッドに置いたときに、品質と快適な表示エクスペリエンスのために、表示がシームレスに調整されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-155">If the user has previously calibrated visuals on the device, the display will be seamlessly adjusted for quality and a comfortable viewing experience when the user puts the device on the head.</span></span> 


## <a name="hololens-v1"></a><span data-ttu-id="1fc7e-156">HoloLens (v1)</span><span class="sxs-lookup"><span data-stu-id="1fc7e-156">HoloLens (v1)</span></span>
<span data-ttu-id="1fc7e-157">IPD (interpupillary distance) を調整することで、ビジュアルの品質を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-157">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="1fc7e-158">セットアップ中</span><span class="sxs-lookup"><span data-stu-id="1fc7e-158">During setup</span></span>

![2番目の手順での IPD の指配置画面](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="1fc7e-160">*2番目の手順での IPD の指配置画面*</span><span class="sxs-lookup"><span data-stu-id="1fc7e-160">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="1fc7e-161">HoloLens では、セットアップ中にビジュアルを調整するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-161">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="1fc7e-162">これにより、デバイスは、ユーザーの[interpupillary 距離](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) に従ってホログラムの表示を調整できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-162">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="1fc7e-163">IPD が正しくない場合は、ホログラムが不安定に見えるか、または正しくない距離にある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-163">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="1fc7e-164">Cortana が自分で導入された後、最初のセットアップ手順は調整です。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-164">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="1fc7e-165">このセットアップ段階では調整手順を完了することをお勧めしますが、移動するには、Cortana に "Skip" というメッセージが表示されるまで待機することでスキップできます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-165">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="1fc7e-166">ユーザーは、1つ目につき6つのターゲットに指を配置するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-166">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="1fc7e-167">このプロセスを通じて、HoloLens はユーザーに適切な IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-167">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="1fc7e-168">新しいユーザーに対して調整を更新または調整する必要がある場合は、調整アプリを使用してセットアップの外部で実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-168">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="1fc7e-169">調整アプリ</span><span class="sxs-lookup"><span data-stu-id="1fc7e-169">Calibration app</span></span>

<span data-ttu-id="1fc7e-170">調整アプリを使用すると、調整をいつでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-170">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="1fc7e-171">調整アプリは既定でインストールされ、[スタート] メニューから、または設定アプリからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-171">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="1fc7e-172">ビジュアルの品質を向上させたり、新しいユーザーの視覚エフェクトを調整したりする場合は、調整をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-172">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="1fc7e-173">**アプリを起動から起動しています**</span><span class="sxs-lookup"><span data-stu-id="1fc7e-173">**Launching the app from Start**</span></span>
1. <span data-ttu-id="1fc7e-174">[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を表示するには、[ブルーム](gestures.md#bloom)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-174">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="1fc7e-175">選択 **+** をすべてのアプリを表示します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-175">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="1fc7e-176">**調整**を開始します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-176">Launch **Calibration**.</span></span>

![シェルからの調整アプリへのアクセス](images/calibration-shell.png)

![起動後にライブキューブとして表示される調整アプリ](images/calibration-livecube-200px.png)

<span data-ttu-id="1fc7e-179">**設定からアプリを起動しています**</span><span class="sxs-lookup"><span data-stu-id="1fc7e-179">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="1fc7e-180">[[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を表示するには、[ブルーム](gestures.md#bloom)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-180">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="1fc7e-181">選択 **+** 場合は、すべてのアプリを表示する**設定**スタートにピン留めされていません。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-181">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="1fc7e-182">起動**設定**。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-182">Launch **Settings**.</span></span>
4. <span data-ttu-id="1fc7e-183">[**システム** > **ユーティリティ**] に移動し、 **[調整を開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-183">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![設定アプリから調整アプリを起動しています](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a><span data-ttu-id="1fc7e-185">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="1fc7e-185">Immersive headsets</span></span>

<span data-ttu-id="1fc7e-186">ヘッドセット内の IPD を変更するには、設定アプリを開き、 **Mixed reality** > **ヘッドセットの表示**に移動して、スライダーコントロールを移動します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-186">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="1fc7e-187">ヘッドセットにリアルタイムの変更が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-187">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="1fc7e-188">IPD がわかっている場合は、optometrist にアクセスするなど、直接入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-188">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="1fc7e-189">この設定を調整するには、[**設定** > ] [**Mixed reality** > **ヘッドセット表示**] [PC] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-189">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="1fc7e-190">ヘッドセットで IPD のカスタマイズがサポートされていない場合、この設定は無効になります。</span><span class="sxs-lookup"><span data-stu-id="1fc7e-190">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fc7e-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fc7e-191">See also</span></span>
* [<span data-ttu-id="1fc7e-192">HoloLens の環境への配慮</span><span class="sxs-lookup"><span data-stu-id="1fc7e-192">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
