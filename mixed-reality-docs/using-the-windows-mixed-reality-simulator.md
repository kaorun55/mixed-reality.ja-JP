---
title: Windows Mixed Reality シミュレーターの使用
description: Windows Mixed Reality シミュレーターを使用すると、Windows Mixed Reality のイマーシブヘッドセットを使用せずに、お使いの PC で mixed reality アプリをテストすることができます。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality、シミュレーター、テスト
ms.openlocfilehash: 686cac4e9ab4b3354767e22cd87d37ffbb508dea
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003298"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="05e75-104">Windows Mixed Reality シミュレーターの使用</span><span class="sxs-lookup"><span data-stu-id="05e75-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="05e75-105">Windows Mixed Reality シミュレーターを使用すると、Windows Mixed Reality のイマーシブヘッドセットを使用せずに、お使いの PC で mixed reality アプリをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="05e75-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="05e75-106">Windows 10 の作成者の更新プログラムから入手できます。</span><span class="sxs-lookup"><span data-stu-id="05e75-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="05e75-107">シミュレーターは[HoloLens エミュレーター](using-the-hololens-emulator.md)に似ていますが、シミュレーターでは仮想マシンが使用されません。</span><span class="sxs-lookup"><span data-stu-id="05e75-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="05e75-108">シミュレーターで実行されているアプリは、イマーシブヘッドセットを使用している場合と同じように、Windows 10 デスクトップユーザーセッションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="05e75-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="05e75-109">通常、イマーシブヘッドセットのセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コントローラーを使用してシミュレートされます。</span><span class="sxs-lookup"><span data-stu-id="05e75-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="05e75-110">アプリをシミュレーターで実行するように変更する必要はなく、イマーシブヘッドセットで実行されていないことはわかりません。</span><span class="sxs-lookup"><span data-stu-id="05e75-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="05e75-111">Windows Mixed Reality シミュレーターの有効化</span><span class="sxs-lookup"><span data-stu-id="05e75-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="05e75-112">開発者向けの設定から**開発者モードを有効にする**-> の更新プログラムとセキュリティ-></span><span class="sxs-lookup"><span data-stu-id="05e75-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="05e75-113">デスクトップから**Mixed Reality ポータル**を起動する</span><span class="sxs-lookup"><span data-stu-id="05e75-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="05e75-114">ポータルを初めて起動する場合は、セットアップエクスペリエンスを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05e75-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="05e75-115">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05e75-115">Click **Get started**</span></span>
   2. <span data-ttu-id="05e75-116">[**同意**する] をクリックして、契約に同意します</span><span class="sxs-lookup"><span data-stu-id="05e75-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="05e75-117">物理デバイスを使用せずにセットアップを続行するには、 **[シミュレーション用に設定 (開発者向け)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05e75-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="05e75-118">[セットアップ] を**クリックして**選択内容を確認します</span><span class="sxs-lookup"><span data-stu-id="05e75-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="05e75-119">Mixed Reality ポータルの左側にある **[開発者向け]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="05e75-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="05e75-120">シミュレーション切り替え**スイッチをオンにする**</span><span class="sxs-lookup"><span data-stu-id="05e75-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="05e75-121">シミュレーションを有効にすると、既定では、シミュレートされた6つの自由可能なコントローラーの左側が有効になります。</span><span class="sxs-lookup"><span data-stu-id="05e75-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="05e75-122">Windows 10 5 月2019更新プログラムの前に、シミュレートされた6自由コントローラーをインストールするには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="05e75-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="05e75-123">表示される場合は、[ユーザーアカウント制御] ダイアログボックスを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="05e75-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="05e75-124">これでシミュレーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="05e75-124">You should now be running with simulation!</span></span>

<span data-ttu-id="05e75-125">設定 で開発者モードを無効にする場合は、まず、Mixed Reality ポータルの **開発者向け** セクションで、シミュレーション切り替えスイッチを **オフ** に切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="05e75-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="05e75-126">混合の現実シミュレーターへのアプリの配置</span><span class="sxs-lookup"><span data-stu-id="05e75-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="05e75-127">シミュレーターは仮想マシンを使用せずにローカル PC で実行されるため、デバッグ時にユニバーサル Windows アプリを**ローカルコンピューター**に配置するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="05e75-127">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="05e75-128">基本的なシミュレーター入力</span><span class="sxs-lookup"><span data-stu-id="05e75-128">Basic simulator input</span></span>

<span data-ttu-id="05e75-129">シミュレーターの制御は、多くの一般的な3D ビデオゲームや[HoloLens エミュレーター](using-the-hololens-emulator.md)とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="05e75-129">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="05e75-130">入力オプションは、キーボード、マウス、または Xbox コントローラーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="05e75-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="05e75-131">シミュレートされたユーザーがイマーシブヘッドセットを装着したときのアクションを指示することによって、シミュレーターを制御します。</span><span class="sxs-lookup"><span data-stu-id="05e75-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="05e75-132">操作を実行すると、シミュレートされたユーザーが移動され、イマーシブヘッドセットの場合と同じように応答するアプリとの対話が行われます。</span><span class="sxs-lookup"><span data-stu-id="05e75-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="05e75-133">**前後左右に歩く** - キーボードの W、A、S、D キーまたは Xbox コントローラーの左スティックを使用します。</span><span class="sxs-lookup"><span data-stu-id="05e75-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="05e75-134">**上下左右を見る** - マウスをクリックしてドラッグするか、キーボードの方向キーを使用するか、Xbox コントローラーの右スティックを使用します。</span><span class="sxs-lookup"><span data-stu-id="05e75-134">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="05e75-135">**コントローラーでのアクションボタンの押下**-マウスを右クリックするか、キーボードの enter キーを押すか、または Xbox コントローラーの A ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="05e75-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="05e75-136">**[ホーム] ボタン**をクリックしてコントローラーを押す-キーボードの Windows キーまたは F2 キーを押すか、Xbox コントローラーの B ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="05e75-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="05e75-137">**スクロール用のコントローラーの移動**-Alt キーを押したままマウスの右ボタンを押し、マウスを上下にドラッグするか、右のトリガーとボタンを押したまま右スティックを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="05e75-137">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="05e75-138">追跡対象のコントローラー</span><span class="sxs-lookup"><span data-stu-id="05e75-138">Tracked controllers</span></span>

<span data-ttu-id="05e75-139">Mixed Reality シミュレーターでは、最大2つのハンド保持された追跡対象モーションコントローラーをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="05e75-139">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="05e75-140">混合 Reality ポータルで切り替えスイッチを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="05e75-140">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="05e75-141">各シミュレートされたコントローラーには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="05e75-141">Each simulated controller has:</span></span>
* <span data-ttu-id="05e75-142">空間内の位置と向き</span><span class="sxs-lookup"><span data-stu-id="05e75-142">Position and orientation in space</span></span>
* <span data-ttu-id="05e75-143">ホーム ボタン</span><span class="sxs-lookup"><span data-stu-id="05e75-143">Home button</span></span>
* <span data-ttu-id="05e75-144">メニュー ボタン</span><span class="sxs-lookup"><span data-stu-id="05e75-144">Menu button</span></span>
* <span data-ttu-id="05e75-145">グリップボタン</span><span class="sxs-lookup"><span data-stu-id="05e75-145">Grip button</span></span>
* <span data-ttu-id="05e75-146">タッチパッド</span><span class="sxs-lookup"><span data-stu-id="05e75-146">Touchpad</span></span>
* <span data-ttu-id="05e75-147">スティック</span><span class="sxs-lookup"><span data-stu-id="05e75-147">Thumbstick</span></span>
* <span data-ttu-id="05e75-148">バッテリレベル</span><span class="sxs-lookup"><span data-stu-id="05e75-148">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="05e75-149">参照</span><span class="sxs-lookup"><span data-stu-id="05e75-149">See also</span></span>
* [<span data-ttu-id="05e75-150">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="05e75-150">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="05e75-151">高度な Mixed Reality シミュレーター入力</span><span class="sxs-lookup"><span data-stu-id="05e75-151">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="05e75-152">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="05e75-152">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="05e75-153">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="05e75-153">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
