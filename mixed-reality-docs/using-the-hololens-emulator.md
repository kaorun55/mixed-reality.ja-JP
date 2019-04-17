---
title: HoloLens のエミュレーターを使用します。
description: HoloLens のエミュレーターを使用して、物理 HoloLens なし、PC 上の複合現実アプリをテストできます。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、エミュレーター
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604101"
---
# <a name="using-the-hololens-emulator"></a><span data-ttu-id="0dbb3-104">HoloLens のエミュレーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-104">Using the HoloLens emulator</span></span>

<span data-ttu-id="0dbb3-105">HoloLens のエミュレーターは、HoloLens の開発ツールセットが付属して物理 HoloLens なし、PC で holographic のアプリをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-105">The HoloLens emulator allows you to test holographic apps on your PC without a physical HoloLens and comes with the HoloLens development toolset.</span></span> <span data-ttu-id="0dbb3-106">エミュレーターでは、HYPER-V 仮想マシンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-106">The emulator uses a Hyper-V virtual machine.</span></span> <span data-ttu-id="0dbb3-107">通常、HoloLens のセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-107">The human and environmental inputs that would usually be read by the sensors on the HoloLens are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="0dbb3-108">アプリでは、エミュレーターで実行するように変更する必要はありませんを実際の HoloLens で実行されていないことがわからない。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-108">Apps don't need to be modified to run on the emulator and don't know that they aren't running on a real HoloLens.</span></span>

<span data-ttu-id="0dbb3-109">デスクトップ Pc の Windows Mixed Reality 没入型 (VR) ヘッドセット アプリやゲームを開発する場合、チェック アウト、 [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)、代わりにデスクトップ ヘッドセットをシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-109">If you're looking to develop Windows Mixed Reality immersive (VR) headset apps or games for desktop PCs, check out the [Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md), which lets you simulate desktop headsets instead.</span></span>

> [!NOTE]
> <span data-ttu-id="0dbb3-110">HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-110">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="installing-the-hololens-emulator"></a><span data-ttu-id="0dbb3-111">HoloLens のエミュレーターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-111">Installing the HoloLens emulator</span></span>

<span data-ttu-id="0dbb3-112">ダウンロード、 [HoloLens (第 1 世代) エミュレーターおよび holographic プロジェクト テンプレート](https://go.microsoft.com/fwlink/?linkid=2065980)します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-112">Download the [HoloLens (1st gen) emulator and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2065980).</span></span>

<span data-ttu-id="0dbb3-113">HoloLens のエミュレーターの以前のビルドのについて、 [HoloLens のエミュレーターのアーカイブ](hololens-emulator-archive.md)ページ。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-113">You can find older builds of the HoloLens emulator on the [HoloLens emulator archive](hololens-emulator-archive.md) page.</span></span>

### <a name="hololens-emulator-system-requirements"></a><span data-ttu-id="0dbb3-114">HoloLens のエミュレーターのシステム要件</span><span class="sxs-lookup"><span data-stu-id="0dbb3-114">HoloLens emulator system requirements</span></span>

<span data-ttu-id="0dbb3-115">HoloLens のエミュレーターでは、HYPER-V に基づいており、ハードウェア高速グラフィックス用の RemoteFx を使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-115">The HoloLens emulator is based on Hyper-V and uses RemoteFx for hardware accelerated graphics.</span></span> <span data-ttu-id="0dbb3-116">エミュレーターを使用するには、PC は、これらのハードウェア要件を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-116">To use the emulator, make sure your PC meets these hardware requirements:</span></span>
* <span data-ttu-id="0dbb3-117">64 ビットの Windows 10 Pro、Enterprise、または教育</span><span class="sxs-lookup"><span data-stu-id="0dbb3-117">64-bit Windows 10 Pro, Enterprise, or Education</span></span> 
    >[!NOTE]
    ><span data-ttu-id="0dbb3-118">Windows 10 Home エディションは、HYPER-V または HoloLens のエミュレーターをサポートしていません</span><span class="sxs-lookup"><span data-stu-id="0dbb3-118">Windows 10 Home edition does not support Hyper-V or the HoloLens emulator</span></span>
* <span data-ttu-id="0dbb3-119">64 ビット CPU</span><span class="sxs-lookup"><span data-stu-id="0dbb3-119">64-bit CPU</span></span>
* <span data-ttu-id="0dbb3-120">CPU と 4 コア (または複数の Cpu と 4 コアの合計)</span><span class="sxs-lookup"><span data-stu-id="0dbb3-120">CPU with 4 cores (or multiple CPUs with a total of 4 cores)</span></span>
* <span data-ttu-id="0dbb3-121">8 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="0dbb3-121">8 GB of RAM or more</span></span>
* <span data-ttu-id="0dbb3-122">次の機能がある必要があります、BIOS で[サポートされていて有効](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span><span class="sxs-lookup"><span data-stu-id="0dbb3-122">In the BIOS, the following features must be [supported and enabled](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span></span>
   * <span data-ttu-id="0dbb3-123">ハードウェア支援による仮想化</span><span class="sxs-lookup"><span data-stu-id="0dbb3-123">Hardware-assisted virtualization</span></span>
   * <span data-ttu-id="0dbb3-124">Second Level Address Translation (SLAT)</span><span class="sxs-lookup"><span data-stu-id="0dbb3-124">Second Level Address Translation (SLAT)</span></span>
   * <span data-ttu-id="0dbb3-125">ハードウェアベースのデータ実行防止 (DEP)</span><span class="sxs-lookup"><span data-stu-id="0dbb3-125">Hardware-based Data Execution Prevention (DEP)</span></span>
* <span data-ttu-id="0dbb3-126">GPU の要件 (エミュレーターでサポートされていない GPU では、機能しますが、大幅に遅くなります)</span><span class="sxs-lookup"><span data-stu-id="0dbb3-126">GPU requirements (the emulator might work with an unsupported GPU, but will be significantly slower)</span></span>
   * <span data-ttu-id="0dbb3-127">DirectX 11.0 以降</span><span class="sxs-lookup"><span data-stu-id="0dbb3-127">DirectX 11.0 or later</span></span>
   * <span data-ttu-id="0dbb3-128">WDDM 1.2 ドライバーまたはそれ以降</span><span class="sxs-lookup"><span data-stu-id="0dbb3-128">WDDM 1.2 driver or later</span></span>

<span data-ttu-id="0dbb3-129">システムが、上記の要件を満たす場合**システムに"HYPER-V"機能が有効になっているか確認してください** コントロール パネル-> プログラム の プログラムと機能の Windows 機能の有効化-> または-> オフことを確認"ハイパー-V"が正常にエミュレーターのインストールの選択されています。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-129">If your system meets the above requirements, **please ensure that the "Hyper-V" feature has been enabled on your system** through Control Panel -> Programs -> Programs and Features -> Turn Windows Features on or off -> ensure that "Hyper-V" is selected for the Emulator installation to be successful.</span></span>

### <a name="installation-troubleshooting"></a><span data-ttu-id="0dbb3-130">インストールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0dbb3-130">Installation troubleshooting</span></span>

<span data-ttu-id="0dbb3-131">必要なエミュレーターのインストール中にエラーが表示可能性があります *「Visual Studio 2015 Update 1 と UWP ツール バージョン 1.2」* します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-131">You may see an error while installing the emulator that you need *"Visual Studio 2015 Update 1 and UWP tools version 1.2"*.</span></span> <span data-ttu-id="0dbb3-132">このエラーの考えられる原因を次の 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-132">There are three possible causes of this error:</span></span>
* <span data-ttu-id="0dbb3-133">Visual Studio (Visual Studio 2017 または Visual Studio 2015 Update 1 またはそれ以降) の最新バージョンではありません。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-133">You do not have a recent enough version of Visual Studio (Visual Studio 2017 or Visual Studio 2015 Update 1 or later).</span></span> <span data-ttu-id="0dbb3-134">これを修正するには、Visual Studio の最新リリースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-134">To correct this, install the latest release of Visual Studio.</span></span>
* <span data-ttu-id="0dbb3-135">Visual Studio の最新バージョンがあることが、ユニバーサル Windows プラットフォーム (UWP) ツールがインストールされている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-135">You have a recent enough version of Visual Studio, but you do not have the Universal Windows Platform (UWP) tools installed.</span></span> <span data-ttu-id="0dbb3-136">これは、Visual Studio のオプション機能です。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-136">This is an optional feature for Visual Studio.</span></span>

<span data-ttu-id="0dbb3-137">エミュレーターで、非-PRO、Enterprise、/教育 SKU の Windows のインストール エラーを表示もまたは HYPER-V 機能がいないかどうかに有効になっています。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-137">You may also see an error installing the emulator on a non-PRO/Enterprise/Education SKU of Windows or if you do not have Hyper-V feature enabled.</span></span>
* <span data-ttu-id="0dbb3-138">参照してください、[システム要件](#hololens-emulator-system-requirements)要件の完全なセットを前の「します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-138">Please read the [system requirements](#hololens-emulator-system-requirements) section above for a complete set of requirements.</span></span>
* <span data-ttu-id="0dbb3-139">システム上で HYPER-V の機能が有効であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-139">Please also ensure that Hyper-V feature has been enabled on your system.</span></span>

## <a name="deploying-apps-to-the-hololens-emulator"></a><span data-ttu-id="0dbb3-140">HoloLens のエミュレーターにアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-140">Deploying apps to the HoloLens emulator</span></span>

1. <span data-ttu-id="0dbb3-141">Visual Studio 2015 でアプリ ソリューションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-141">Load your app solution in Visual Studio 2015.</span></span>
    >[!NOTE]
    ><span data-ttu-id="0dbb3-142">Unity を使用する場合は、Unity からプロジェクトをビルドし、通常どおり Visual Studio に、作成されたソリューションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-142">When using Unity, build your project from Unity and then load the built solution into Visual Studio as usual.</span></span>
2. <span data-ttu-id="0dbb3-143">プラットフォームに設定されていることを確認**x86**します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-143">Ensure the Platform is set to **x86**.</span></span>
3. <span data-ttu-id="0dbb3-144">選択、 **HoloLens のエミュレーター**デバッグのターゲット デバイスとして。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-144">Select the **HoloLens Emulator** as the target device for debugging.</span></span>
4. <span data-ttu-id="0dbb3-145">移動して**デバッグ > [デバッグ開始]** またはキーを押します**F5**エミュレーターを起動してデバッグ用のアプリをデプロイします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-145">Go to **Debug > Start Debugging** or press **F5** to launch the emulator and deploy your app for debugging.</span></span>

<span data-ttu-id="0dbb3-146">エミュレーターは、最初に起動するときに起動する、1 分以上かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-146">The emulator may take a minute or more to boot when you first start it.</span></span> <span data-ttu-id="0dbb3-147">開いたままにしておく、エミュレーター、デバッグ セッション中に実行中のエミュレーターにアプリをすばやくデプロイできるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-147">We recommend that you keep the emulator open during your debugging session so you can quickly deploy apps to the running emulator.</span></span>

## <a name="basic-emulator-input"></a><span data-ttu-id="0dbb3-148">基本的なエミュレーターの入力</span><span class="sxs-lookup"><span data-stu-id="0dbb3-148">Basic emulator input</span></span>

<span data-ttu-id="0dbb3-149">エミュレーターの制御は、多くの一般的な 3 D ビデオ ゲームによく似ています。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-149">Controlling the emulator is very similar to many common 3D video games.</span></span> <span data-ttu-id="0dbb3-150">入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-150">There are input options available using the keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="0dbb3-151">エミュレーターを制御するには、ソックスを着けずに、HoloLens のシミュレートされたユーザーの操作をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-151">You control the emulator by directing the actions of a simulated user wearing a HoloLens.</span></span> <span data-ttu-id="0dbb3-152">周囲のシミュレートされたユーザーと、エミュレーターで実行されているアプリが実際のデバイスでこれらと同じように応答するアクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-152">Your actions move that simulated user around and apps running in the emulator respond like they would on a real device.</span></span>
* <span data-ttu-id="0dbb3-153">**転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-153">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="0dbb3-154">**検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-154">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="0dbb3-155">**エア タップ ジェスチャ**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-155">**Air tap gesture** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="0dbb3-156">**ジェスチャを咲かせること**- には、キーボードの Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-156">**Bloom gesture** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="0dbb3-157">**スクロールの移動を渡す**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-157">**Hand movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="anatomy-of-the-hololens-emulator"></a><span data-ttu-id="0dbb3-158">HoloLens のエミュレーターの構造</span><span class="sxs-lookup"><span data-stu-id="0dbb3-158">Anatomy of the HoloLens emulator</span></span>

### <a name="main-window"></a><span data-ttu-id="0dbb3-159">メイン ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="0dbb3-159">Main window</span></span>

<span data-ttu-id="0dbb3-160">エミュレーターを起動すると、HoloLens の OS を表示するウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-160">When the emulator launches, you will see a window which displays the HoloLens OS.</span></span>

![HoloLens のエミュレーターのメイン ウィンドウ](images/emulator-890px.png)

### <a name="toolbar"></a><span data-ttu-id="0dbb3-162">ツール バー</span><span class="sxs-lookup"><span data-stu-id="0dbb3-162">Toolbar</span></span>

<span data-ttu-id="0dbb3-163">メイン ウィンドウの右側には、エミュレーター ツールバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-163">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="0dbb3-164">ツールバーには、次のボタンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-164">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="0dbb3-165">![ある閉じるアイコン](images/emulator-close.png)**閉じる**:エミュレーターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-165">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="0dbb3-166">![最小化アイコン](images/emulator-minimize.png)**最小化**:エミュレーターのウィンドウを最小化します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-166">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="0dbb3-167">![人間の入力アイコン](images/emulator-control.png)**人間入力**:マウスとキーボードが人間をシミュレートするために使用される[エミュレーターへの入力](#basic-emulator-input)します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-167">![Human input icon](images/emulator-control.png) **Human Input**: Mouse and Keyboard are used to simulate human [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="0dbb3-168">![キーボードとマウス入力アイコン](images/emulator-input.png)**キーボードとマウス入力**:キーボードとマウスの入力として渡されます HoloLens OS に直接キーボードとマウスのイベント、Bluetooth キーボードとマウスを接続する場合と同じ。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-168">![Keyboard and mouse input icon](images/emulator-input.png) **Keyboard and Mouse Input**: Keyboard and mouse input are passed directly to the HoloLens OS as keyboard and mouse events as if you connected a Bluetooth keyboard and mouse.</span></span>
* <span data-ttu-id="0dbb3-169">![画面のアイコンに合わせる](images/emulator-fit.png)**画面に合わせる**:エミュレーターの画面に収まるようにします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-169">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="0dbb3-170">![[ズーム] アイコン](images/emulator-zoom.png)**ズーム**:大きくしたり小さく、エミュレーターを作成します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-170">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="0dbb3-171">![ヘルプ アイコン](images/emulator-help.png)**ヘルプ**:エミュレーターのヘルプを開きます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-171">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="0dbb3-172">![開いているデバイスのポータル アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-172">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="0dbb3-173">![ツール アイコン](images/emulator-tools.png)**ツール**:開く、**追加ツール**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-173">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-tab"></a><span data-ttu-id="0dbb3-174">シミュレーション タブ</span><span class="sxs-lookup"><span data-stu-id="0dbb3-174">Simulation tab</span></span>

<span data-ttu-id="0dbb3-175">内で、既定のタブ、**追加ツール**ウィンドウは、**シミュレーション**タブ。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-175">The default tab within the **Additional Tools** pane is the **Simulation** tab.</span></span>

![HoloLens のエミュレーター ' 追加ツール ウィンドウ](images/emulator-simulation-500px.png)

<span data-ttu-id="0dbb3-177">シミュレーションのタブには、エミュレーター内での HoloLens の OS を促進するために使用するシミュレートされたセンサーの現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-177">The Simulation tab shows the current state of the simulated sensors used to drive the HoloLens OS within the emulator.</span></span> <span data-ttu-id="0dbb3-178">シミュレーション タブの任意の値を合わせると、その値を制御する方法を説明するヒントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-178">Hovering over any value in the Simulation tab will provide a tooltip describing how to control that value.</span></span>

### <a name="room-tab"></a><span data-ttu-id="0dbb3-179">ルーム タブ</span><span class="sxs-lookup"><span data-stu-id="0dbb3-179">Room tab</span></span>

<span data-ttu-id="0dbb3-180">エミュレーターでは、シミュレートされた「ルーム」から空間マッピング メッシュの形式で世界中の入力をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-180">The emulator simulates world input in the form of the spatial mapping mesh from simulated "rooms".</span></span> <span data-ttu-id="0dbb3-181">このタブを使用して、どの部屋を既定のルームではなく読み込むを選択できます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-181">This tab lets you pick which room to load instead of the default room.</span></span>

![HoloLens のエミュレーター 'ルーム' タブ](images/emulator-room-500px.png)

<span data-ttu-id="0dbb3-183">シミュレートされたルームは、複数の環境でアプリをテストするため便利です。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-183">Simulated rooms are useful for testing your app in multiple environments.</span></span> <span data-ttu-id="0dbb3-184">ルームのいくつかのエミュレーターが付属していて、%programfiles(x86) %\Program Files (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 検索は、エミュレーションをインストールするとします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-184">Several rooms are shipped with the emulator and once you install the emulation, you will find them in %ProgramFiles(x86)%\Program Files (x86)\Microsoft XDE\10.0.11082.0\Plugins\Rooms.</span></span> <span data-ttu-id="0dbb3-185">すべてのこれらのルームは、HoloLens を使用して実際の環境でキャプチャされました。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-185">All of these rooms were captured in real environments using a HoloLens:</span></span>
* <span data-ttu-id="0dbb3-186">**DefaultRoom.xef** -小さなリビング ルーム、テレビ、コーヒー テーブルでは、2 つの sofas とします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-186">**DefaultRoom.xef** - A small living room with a TV, coffee table, and two sofas.</span></span> <span data-ttu-id="0dbb3-187">エミュレーターを起動すると、既定で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-187">Loaded by default when you start the emulator.</span></span>
* <span data-ttu-id="0dbb3-188">**Bedroom1.xef** -小規模の寝室、デスクとします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-188">**Bedroom1.xef** - A small bedroom with a desk.</span></span>
* <span data-ttu-id="0dbb3-189">**Bedroom2.xef** -寝室クイーン サイズ ベッド、引き出しドレッサー、nightstands、および持ち込んでクローゼットを使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-189">**Bedroom2.xef** - A bedroom with a queen size bed, dresser, nightstands, and walk-in closet.</span></span>
* <span data-ttu-id="0dbb3-190">**GreatRoom.xef** -大きな空き領域優れたルーム リビング ルーム、レストランのテーブルおよびキッチンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-190">**GreatRoom.xef** - A large open space great room with living room, dining table, and kitchen.</span></span>
* <span data-ttu-id="0dbb3-191">**LivingRoom.xef** -、暖炉、ソファー、armchairs、リビング ルームおよびハードカバー花瓶とします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-191">**LivingRoom.xef** - A living room with a fireplace, sofa, armchairs, and a coffee table with a vase.</span></span>

<span data-ttu-id="0dbb3-192">シミュレーションのページを使用して、エミュレーターで使用する独自の部屋を記録することも、 [Windows Device Portal](using-the-windows-device-portal.md) HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-192">You can also record your own rooms to use in the emulator using the Simulation page of the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens.</span></span>

<span data-ttu-id="0dbb3-193">エミュレーターでは、ホログラムをレンダリングして、ホログラムの背後にあるシミュレートされた部屋は表示されませんのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-193">On the emulator, you will only see holograms that you render and you will not see the simulated room behind the holograms.</span></span> <span data-ttu-id="0dbb3-194">これは、両方を表示する実際の HoloLens とは対照的ブレンドします。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-194">This is in contrast to the real HoloLens where you see both blended together.</span></span> <span data-ttu-id="0dbb3-195">HoloLens のエミュレーターのシミュレートされたルームが表示する場合は、シーン内の空間マッピングのメッシュを表示するために、アプリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-195">If you want to see the simulated room in the HoloLens emulator, you will need to update your app to render the spatial mapping mesh in the scene.</span></span>

### <a name="account-tab"></a><span data-ttu-id="0dbb3-196">[アカウント] タブ</span><span class="sxs-lookup"><span data-stu-id="0dbb3-196">Account Tab</span></span>

<span data-ttu-id="0dbb3-197">[アカウント] タブでは、Microsoft アカウントでサインインにエミュレーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-197">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="0dbb3-198">これは、アカウントでサインインするユーザーを必要とする API をテストするため便利です。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-198">This is useful for testing API's that require the user to be signed-in with an account.</span></span> <span data-ttu-id="0dbb3-199">このページで、ボックスをオンにした後でサインインすること、エミュレーターのそれ以降の起動時に尋ねます、HoloLens が開始されます、ユーザーが初めてと同様です。</span><span class="sxs-lookup"><span data-stu-id="0dbb3-199">After checking the box on this page, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dbb3-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dbb3-200">See also</span></span>
* [<span data-ttu-id="0dbb3-201">HoloLens のエミュレーターと Mixed Reality シミュレーターの高度な入力</span><span class="sxs-lookup"><span data-stu-id="0dbb3-201">Advanced HoloLens Emulator and Mixed Reality Simulator input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="0dbb3-202">HoloLens のエミュレーターのソフトウェアの履歴</span><span class="sxs-lookup"><span data-stu-id="0dbb3-202">HoloLens emulator software history</span></span>](hololens-emulator-archive.md)
* [<span data-ttu-id="0dbb3-203">Unity での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="0dbb3-203">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="0dbb3-204">DirectX での空間のマッピング</span><span class="sxs-lookup"><span data-stu-id="0dbb3-204">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
