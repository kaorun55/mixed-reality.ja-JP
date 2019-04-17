---
title: Windows Mixed Reality シミュレーターの使用
description: Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows の混合実際には、シミュレーターのテスト
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603637"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="abb44-104">Windows Mixed Reality シミュレーターの使用</span><span class="sxs-lookup"><span data-stu-id="abb44-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="abb44-105">Windows Mixed Reality シミュレーターでは、Windows Mixed Reality イマーシブ ヘッドセットなし、PC 上の複合現実アプリをテストできます。</span><span class="sxs-lookup"><span data-stu-id="abb44-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="abb44-106">以降、Windows 10 Creators Update で利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="abb44-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="abb44-107">シミュレーターと似ています、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)できたとして、シミュレーターは、仮想マシンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="abb44-107">The simulator is similar to the [HoloLens emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="abb44-108">シミュレーターで実行されているアプリは、イマーシブ ヘッドセットを使用していた場合と同様、Windows 10 デスクトップ ユーザーのセッションで実行します。</span><span class="sxs-lookup"><span data-stu-id="abb44-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="abb44-109">通常、イマーシブ ヘッドセットのセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="abb44-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="abb44-110">アプリでは、シミュレーターで実行するように変更する必要はありませんをイマーシブ ヘッドセットで実行されていないことがわからない。</span><span class="sxs-lookup"><span data-stu-id="abb44-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="abb44-111">Windows Mixed Reality シミュレーターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="abb44-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="abb44-112">**開発者モードを有効にする**設定から]、[更新とセキュリティは、開発者向け]-> [</span><span class="sxs-lookup"><span data-stu-id="abb44-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="abb44-113">起動、 **Mixed Reality ポータル**デスクトップから</span><span class="sxs-lookup"><span data-stu-id="abb44-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="abb44-114">初めてポータルを起動する場合は、セットアップ エクスペリエンスを経由する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb44-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="abb44-115">クリックして**を開始します。**</span><span class="sxs-lookup"><span data-stu-id="abb44-115">Click **Get started**</span></span>
   2. <span data-ttu-id="abb44-116">クリックして**同意**契約に同意するには</span><span class="sxs-lookup"><span data-stu-id="abb44-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="abb44-117">クリックして**シミュレーション (開発者) を設定する**物理デバイスがなくてもセットアップを続行するには</span><span class="sxs-lookup"><span data-stu-id="abb44-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="abb44-118">クリックして**セットアップ**を確定するには</span><span class="sxs-lookup"><span data-stu-id="abb44-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="abb44-119">をクリックして、**開発者向け**Mixed Reality ポータルの左側にあるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="abb44-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="abb44-120">シミュレーションのトグル スイッチを有効に**で**</span><span class="sxs-lookup"><span data-stu-id="abb44-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="abb44-121">Admin アクセス許可が必要であり、表示されるユーザー アカウント制御ダイアログを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb44-121">This requires admin permissions and you must accept the User Account Control dialog that appears</span></span>

<span data-ttu-id="abb44-122">今すぐ、シミュレーションを実行する必要があります!</span><span class="sxs-lookup"><span data-stu-id="abb44-122">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="abb44-123">Mixed Reality シミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="abb44-123">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="abb44-124">ユニバーサル Windows アプリをデプロイするため、シミュレーターを実行せず、仮想マシンのローカル コンピューター上だけことができます、**ローカル マシン**をデバッグするとき。</span><span class="sxs-lookup"><span data-stu-id="abb44-124">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="abb44-125">基本的なシミュレーターの入力</span><span class="sxs-lookup"><span data-stu-id="abb44-125">Basic simulator input</span></span>

<span data-ttu-id="abb44-126">多くの一般的な 3 D ビデオ ゲームによく似ていますが、シミュレーターを制御して、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)します。</span><span class="sxs-lookup"><span data-stu-id="abb44-126">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="abb44-127">入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abb44-127">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="abb44-128">シミュレーターを制御するには、ソックスを着けずに、イマーシブ ヘッドセット シミュレートされたユーザーの操作を送信します。</span><span class="sxs-lookup"><span data-stu-id="abb44-128">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="abb44-129">操作は、シミュレートされたユーザーを移動し、応答、イマーシブ ヘッドセットの場合とするアプリとのやり取りが発生します。</span><span class="sxs-lookup"><span data-stu-id="abb44-129">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="abb44-130">**転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。</span><span class="sxs-lookup"><span data-stu-id="abb44-130">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="abb44-131">**検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="abb44-131">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="abb44-132">**コント ローラーのアクション ボタンを押す**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="abb44-132">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="abb44-133">**ホーム コント ローラー上のボタンを押す**- には、キーボードの Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="abb44-133">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="abb44-134">**スクロールのためにコント ローラー移動**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="abb44-134">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="abb44-135">追跡コント ローラー</span><span class="sxs-lookup"><span data-stu-id="abb44-135">Tracked controllers</span></span>

<span data-ttu-id="abb44-136">Mixed Reality シミュレーターでは、最大で 2 つのハンドヘルド履歴モーション コント ローラーをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="abb44-136">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="abb44-137">Mixed Reality ポータルのトグル スイッチを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="abb44-137">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="abb44-138">シミュレートされた各コント ローラーがあります。</span><span class="sxs-lookup"><span data-stu-id="abb44-138">Each simulated controller has:</span></span>
* <span data-ttu-id="abb44-139">空間内の位置</span><span class="sxs-lookup"><span data-stu-id="abb44-139">Position in space</span></span>
* <span data-ttu-id="abb44-140">[ホーム] ボタン</span><span class="sxs-lookup"><span data-stu-id="abb44-140">Home button</span></span>
* <span data-ttu-id="abb44-141">メニュー ボタン</span><span class="sxs-lookup"><span data-stu-id="abb44-141">Menu button</span></span>
* <span data-ttu-id="abb44-142">グリップのボタン</span><span class="sxs-lookup"><span data-stu-id="abb44-142">Grip button</span></span>
* <span data-ttu-id="abb44-143">タッチパッド</span><span class="sxs-lookup"><span data-stu-id="abb44-143">Touchpad</span></span>

## <a name="see-also"></a><span data-ttu-id="abb44-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="abb44-144">See also</span></span>
* [<span data-ttu-id="abb44-145">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="abb44-145">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="abb44-146">Mixed Reality シミュレーターの入力を高度な</span><span class="sxs-lookup"><span data-stu-id="abb44-146">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="abb44-147">Unity での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="abb44-147">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="abb44-148">DirectX での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="abb44-148">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
