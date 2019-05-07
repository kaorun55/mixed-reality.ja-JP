---
title: Windows Mixed Reality シミュレーターの使用
description: Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows の混合実際には、シミュレーターのテスト
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580701"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="28946-104">Windows Mixed Reality シミュレーターの使用</span><span class="sxs-lookup"><span data-stu-id="28946-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="28946-105">Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。</span><span class="sxs-lookup"><span data-stu-id="28946-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="28946-106">以降、Windows 10 Creators Update で利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="28946-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="28946-107">シミュレーターと似ています、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)できたとして、シミュレーターは、仮想マシンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="28946-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="28946-108">シミュレーターで実行されているアプリは、イマーシブ ヘッドセットを使用していた場合と同様、Windows 10 デスクトップ ユーザーのセッションで実行します。</span><span class="sxs-lookup"><span data-stu-id="28946-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="28946-109">通常、イマーシブ ヘッドセットのセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="28946-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="28946-110">アプリでは、シミュレーターで実行するように変更する必要はありませんをイマーシブ ヘッドセットで実行されていないことがわからない。</span><span class="sxs-lookup"><span data-stu-id="28946-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="28946-111">Windows Mixed Reality シミュレーターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="28946-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="28946-112">**開発者モードを有効にする**設定から]、[更新とセキュリティは、開発者向け]-> [</span><span class="sxs-lookup"><span data-stu-id="28946-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="28946-113">起動、 **Mixed Reality ポータル**デスクトップから</span><span class="sxs-lookup"><span data-stu-id="28946-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="28946-114">初めてポータルを起動する場合は、セットアップ エクスペリエンスを経由する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28946-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="28946-115">クリックして**を開始します。**</span><span class="sxs-lookup"><span data-stu-id="28946-115">Click **Get started**</span></span>
   2. <span data-ttu-id="28946-116">クリックして**同意**契約に同意するには</span><span class="sxs-lookup"><span data-stu-id="28946-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="28946-117">クリックして**シミュレーション (開発者) を設定する**物理デバイスがなくてもセットアップを続行するには</span><span class="sxs-lookup"><span data-stu-id="28946-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="28946-118">クリックして**セットアップ**を確定するには</span><span class="sxs-lookup"><span data-stu-id="28946-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="28946-119">をクリックして、**開発者向け**Mixed Reality ポータルの左側にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="28946-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="28946-120">シミュレーションのトグル スイッチを有効に**で**</span><span class="sxs-lookup"><span data-stu-id="28946-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="28946-121">シミュレーションを有効にすると、インストールし、既定で左側シミュレーションの 6-自由度のコント ローラーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="28946-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="28946-122">前に、Windows 10 の月 2019年シミュレートされた 6-自由度のコント ローラーのインストール、更新プログラムが必要です管理者のアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="28946-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="28946-123">いずれかが表示された場合は、ユーザー アカウント制御 ダイアログを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="28946-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="28946-124">今すぐ、シミュレーションを実行する必要があります!</span><span class="sxs-lookup"><span data-stu-id="28946-124">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="28946-125">Mixed Reality シミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="28946-125">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="28946-126">ユニバーサル Windows アプリをデプロイするため、シミュレーターを実行せず、仮想マシンのローカル コンピューター上だけことができます、**ローカル マシン**をデバッグするとき。</span><span class="sxs-lookup"><span data-stu-id="28946-126">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="28946-127">基本的なシミュレーターの入力</span><span class="sxs-lookup"><span data-stu-id="28946-127">Basic simulator input</span></span>

<span data-ttu-id="28946-128">多くの一般的な 3 D ビデオ ゲームによく似ていますが、シミュレーターを制御して、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)します。</span><span class="sxs-lookup"><span data-stu-id="28946-128">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="28946-129">入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="28946-129">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="28946-130">シミュレーターを制御するには、ソックスを着けずに、イマーシブ ヘッドセット シミュレートされたユーザーの操作を送信します。</span><span class="sxs-lookup"><span data-stu-id="28946-130">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="28946-131">操作は、シミュレートされたユーザーを移動し、応答、イマーシブ ヘッドセットの場合とするアプリとのやり取りが発生します。</span><span class="sxs-lookup"><span data-stu-id="28946-131">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="28946-132">**転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。</span><span class="sxs-lookup"><span data-stu-id="28946-132">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="28946-133">**検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="28946-133">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="28946-134">**コント ローラーのアクション ボタンを押す**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="28946-134">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="28946-135">**ホーム コント ローラー上のボタンを押す**- には、キーボードの Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="28946-135">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="28946-136">**スクロールのためにコント ローラー移動**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="28946-136">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="28946-137">追跡コント ローラー</span><span class="sxs-lookup"><span data-stu-id="28946-137">Tracked controllers</span></span>

<span data-ttu-id="28946-138">Mixed Reality シミュレーターでは、最大で 2 つのハンドヘルド履歴モーション コント ローラーをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="28946-138">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="28946-139">Mixed Reality ポータルのトグル スイッチを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="28946-139">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="28946-140">シミュレートされた各コント ローラーがあります。</span><span class="sxs-lookup"><span data-stu-id="28946-140">Each simulated controller has:</span></span>
* <span data-ttu-id="28946-141">位置と向きを領域</span><span class="sxs-lookup"><span data-stu-id="28946-141">Position and orientation in space</span></span>
* <span data-ttu-id="28946-142">[ホーム] ボタン</span><span class="sxs-lookup"><span data-stu-id="28946-142">Home button</span></span>
* <span data-ttu-id="28946-143">メニュー ボタン</span><span class="sxs-lookup"><span data-stu-id="28946-143">Menu button</span></span>
* <span data-ttu-id="28946-144">グリップのボタン</span><span class="sxs-lookup"><span data-stu-id="28946-144">Grip button</span></span>
* <span data-ttu-id="28946-145">タッチパッド</span><span class="sxs-lookup"><span data-stu-id="28946-145">Touchpad</span></span>
* <span data-ttu-id="28946-146">スティック</span><span class="sxs-lookup"><span data-stu-id="28946-146">Thumbstick</span></span>
* <span data-ttu-id="28946-147">バッテリ レベル</span><span class="sxs-lookup"><span data-stu-id="28946-147">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="28946-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="28946-148">See also</span></span>
* [<span data-ttu-id="28946-149">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="28946-149">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="28946-150">Mixed Reality シミュレーターの入力を高度な</span><span class="sxs-lookup"><span data-stu-id="28946-150">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="28946-151">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="28946-151">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="28946-152">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="28946-152">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
