---
title: リリースノート-2016 年8月
description: Windows 10 記念日リリースの HoloLens リリースノート (秋 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リリースノート、os、プラットフォーム、機能、商用スイート
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438096"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="c83f1-104">リリースノート-2016 年8月</span><span class="sxs-lookup"><span data-stu-id="c83f1-104">Release notes - August 2016</span></span>

<span data-ttu-id="c83f1-105">HoloLens チームは、作業の優先順位を決定するために、Windows Insider プログラムの開発者からのフィードバックをリッスンしています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="c83f1-106">フィードバックハブ、[開発者フォーラム](https://forums.hololens.com)、Twitter から、 [@HoloLens](https://twitter.com/hololens)を通じて[フィードバック](give-us-feedback.md)を引き続きお寄せください。</span><span class="sxs-lookup"><span data-stu-id="c83f1-106">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="c83f1-107">Windows 10 が記念日の更新を採用しているため、HoloLens チームは holographic エクスペリエンスにさらなる改善を提供しています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="c83f1-108">この更新プログラムでは、Microsoft HoloLens 商用 Suite で利用できる、ビジネスによって要求された機能の主な修正、改善、導入に焦点を絞っています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="c83f1-109">**最新リリース:** Windows Holographic 8 月2016更新プログラム (**10.0.14393.0**、Windows 10 記念日リリース)</span><span class="sxs-lookup"><span data-stu-id="c83f1-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="c83f1-110">[現在のリリースに更新](updating-hololens.md)するには、*設定*アプリを開き、[ *update & Security*] にアクセスして、[*更新プログラムの確認*] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c83f1-110">To [update to the current release](updating-hololens.md), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="c83f1-111">新機能</span><span class="sxs-lookup"><span data-stu-id="c83f1-111">New features</span></span>

<span data-ttu-id="c83f1-112">**プロセスデバッグにアタッチ**HoloLens では、プロセス間のデバッグがサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="c83f1-113">Visual Studio 2015 Update 3 を使用して、HoloLens で実行中のアプリに接続し、[デバッグを開始](using-visual-studio.md#debugging-an-installed-or-running-app)することができます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](using-visual-studio.md#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="c83f1-114">これは、Visual Studio プロジェクトから配置する必要がない場合に機能します。</span><span class="sxs-lookup"><span data-stu-id="c83f1-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="c83f1-115">**HoloLens エミュレーターを更新しました**また、更新されたバージョンの HoloLens エミュレーターもリリースしました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="c83f1-116">**ゲームパッドのサポート**HoloLens で Bluetooth ゲームパッドを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="c83f1-117">新しくリリースされた Xbox ワイヤレスコントローラーは、Bluetooth 機能を搭載しており、お気に入りのゲーム用ゲームやアプリの再生に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="c83f1-118">Xbox ワイヤレスコントローラーを HoloLens に接続する前に、[コントローラーの更新プログラム](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c83f1-118">A [controller update](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="c83f1-119">Xbox ワイヤレスコントローラーは、[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) と [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="c83f1-120">Bluetooth コントローラーの追加モデルには、Windows の[ゲーム入力](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)API を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="c83f1-121">機能強化と修正</span><span class="sxs-lookup"><span data-stu-id="c83f1-121">Improvements and fixes</span></span>

<span data-ttu-id="c83f1-122">Microsoft は、Windows 10 の記念日更新プログラムとの同期を行っています。そのため、HoloLens 固有の修正プログラムに加えて、プラットフォームの信頼性とパフォーマンスを向上させるために、Windows update のすべての利点も受けています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the HoloLens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="c83f1-123">フィードバックは非常に重要であり、リリースの修正のために優先順位が付けられています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="c83f1-124">次のエクスペリエンスが改善されました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="c83f1-125">ログインエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="c83f1-125">log in experiences.</span></span>
* <span data-ttu-id="c83f1-126">workplace join。</span><span class="sxs-lookup"><span data-stu-id="c83f1-126">workplace join.</span></span>
* <span data-ttu-id="c83f1-127">デバイスの電源状態遷移の電力効率。</span><span class="sxs-lookup"><span data-stu-id="c83f1-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="c83f1-128">Mixed Reality キャプチャによる安定性。</span><span class="sxs-lookup"><span data-stu-id="c83f1-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="c83f1-129">Bluetooth 接続の信頼性</span><span class="sxs-lookup"><span data-stu-id="c83f1-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="c83f1-130">マルチアプリシナリオにおけるホログラムの永続性。</span><span class="sxs-lookup"><span data-stu-id="c83f1-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="c83f1-131">次の問題が修正されました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="c83f1-132">Visual Studio プロファイラーとグラフィックスデバッガーは接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="c83f1-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="c83f1-133">写真 & ドキュメントは、デバイスポータルのエクスプローラーに表示されません。</span><span class="sxs-lookup"><span data-stu-id="c83f1-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="c83f1-134">アプリバーは、調整モードでカーソルが上に置かれたときにフラッシュできます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="c83f1-135">調整モードでは、視線が上向きのドットカーソルが4方向のカーソルに変わります。</span><span class="sxs-lookup"><span data-stu-id="c83f1-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="c83f1-136">"Cortana play music" さんは Groove を起動しません。</span><span class="sxs-lookup"><span data-stu-id="c83f1-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="c83f1-137">以前の更新の後、「ホーム」と言うと、ピンパネルが正しく表示されません。</span><span class="sxs-lookup"><span data-stu-id="c83f1-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="c83f1-138">Microsoft HoloLens 商用スイートの概要</span><span class="sxs-lookup"><span data-stu-id="c83f1-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="c83f1-139">Microsoft HoloLens 商用 Suite は、エンタープライズ展開の準備ができています。</span><span class="sxs-lookup"><span data-stu-id="c83f1-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="c83f1-140">初期のビジネスパートナーから、高度に要求された[商用機能](commercial-features.md)がいくつか追加されました。</span><span class="sxs-lookup"><span data-stu-id="c83f1-140">We've added several highly requested [commercial features](commercial-features.md) from our early business partners.</span></span>

<span data-ttu-id="c83f1-141">Microsoft HoloLens 商用スイートを購入するには、ローカル Microsoft アカウントマネージャーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="c83f1-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="c83f1-142">主要商用機能</span><span class="sxs-lookup"><span data-stu-id="c83f1-142">Key Commercial Features</span></span> 

* <span data-ttu-id="c83f1-143">**キオスクモード。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-143">**Kiosk mode.**</span></span> <span data-ttu-id="c83f1-144">HoloLens キオスクモードでは、実行するアプリを制限してデモやショーケースを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="c83f1-145">![キオスクモードでは、HoloLens は選択したアプリに直接起動します。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="c83f1-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="c83f1-146">**HoloLens 用のモバイルデバイス管理 (MDM)。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="c83f1-147">IT 部門は、Microsoft Intune などのソリューションを使用して、複数の HoloLens デバイスを同時に管理できます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="c83f1-148">設定の管理、インストールするアプリの選択、組織のニーズに合わせたセキュリティ構成の設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="c83f1-149">HoloLens のモバイルデバイス管理 ![、複数のデバイスにわたるエンタープライズレベルのデバイス管理を提供します。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="c83f1-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="c83f1-150">**ビジネス向け Windows Update。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-150">**Windows Update for Business.**</span></span> <span data-ttu-id="c83f1-151">デバイスに対するオペレーティングシステムの更新と、長期的なサービスブランチのサポートを制御します。</span><span class="sxs-lookup"><span data-stu-id="c83f1-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="c83f1-152">**データのセキュリティ。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-152">**Data security.**</span></span> <span data-ttu-id="c83f1-153">HoloLens で BitLocker データ暗号化が有効になっているため、他の Windows デバイスと同じレベルのセキュリティ保護が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="c83f1-154">**職場へのアクセス。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-154">**Work access.**</span></span> <span data-ttu-id="c83f1-155">組織内のすべてのユーザーが、HoloLens の仮想プライベートネットワークを介して企業ネットワークにリモート接続できます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="c83f1-156">HoloLens は、資格情報を必要とする Wi-fi ネットワークにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="c83f1-157">**ビジネス向け Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="c83f1-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="c83f1-158">また、IT 部門は、特定の HoloLens 使用量について会社のアプリのみを含むエンタープライズプライベートストアをセットアップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c83f1-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="c83f1-159">エンタープライズユーザーの選択したグループにエンタープライズソフトウェアを安全に配布します。</span><span class="sxs-lookup"><span data-stu-id="c83f1-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="c83f1-160">開発エディションと商用スイート</span><span class="sxs-lookup"><span data-stu-id="c83f1-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="c83f1-161">機能</span><span class="sxs-lookup"><span data-stu-id="c83f1-161">Features</span></span></th><th><span data-ttu-id="c83f1-162">開発エディション</span><span class="sxs-lookup"><span data-stu-id="c83f1-162">Development Edition</span></span></th><th><span data-ttu-id="c83f1-163">商用スイート</span><span class="sxs-lookup"><span data-stu-id="c83f1-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="c83f1-164">デバイスの暗号化 (Bitlocker)</span><span class="sxs-lookup"><span data-stu-id="c83f1-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-165">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-166">仮想プライベート ネットワーク (VPN)</span><span class="sxs-lookup"><span data-stu-id="c83f1-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-167">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-168"><a href="using-the-windows-device-portal.md#kiosk-mode">キオスクモード</a></span><span class="sxs-lookup"><span data-stu-id="c83f1-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-169">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="c83f1-170">管理と展開</span><span class="sxs-lookup"><span data-stu-id="c83f1-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="c83f1-171">モバイル デバイス管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="c83f1-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="c83f1-172">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-173">登録解除をブロックする機能</span><span class="sxs-lookup"><span data-stu-id="c83f1-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-174">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-175">証明書ベースの会社の Wi-fi アクセス</span><span class="sxs-lookup"><span data-stu-id="c83f1-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-176">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-177">Microsoft Store (コンシューマー)</span><span class="sxs-lookup"><span data-stu-id="c83f1-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-178">者</span><span class="sxs-lookup"><span data-stu-id="c83f1-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-179">MDM を使用したフィルター処理</span><span class="sxs-lookup"><span data-stu-id="c83f1-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">ビジネスストアポータル</a></span><span class="sxs-lookup"><span data-stu-id="c83f1-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-181">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="c83f1-182">セキュリティと ID</span><span class="sxs-lookup"><span data-stu-id="c83f1-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="c83f1-183">Azure Active Directory を使用したログイン (AAD)</span><span class="sxs-lookup"><span data-stu-id="c83f1-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-184">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-185">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-186">Microsoft アカウント (MSA) を使用してログインする</span><span class="sxs-lookup"><span data-stu-id="c83f1-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-187">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-188">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-189">PIN のロック解除を含む次世代の資格情報</span><span class="sxs-lookup"><span data-stu-id="c83f1-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-190">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-191">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">セキュア ブート</a></span><span class="sxs-lookup"><span data-stu-id="c83f1-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-193">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-194">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="c83f1-195">サービスとサポート</span><span class="sxs-lookup"><span data-stu-id="c83f1-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="c83f1-196">自動的にシステムを更新する</span><span class="sxs-lookup"><span data-stu-id="c83f1-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-197">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c83f1-198">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">ビジネス向け Windows Update</a></span><span class="sxs-lookup"><span data-stu-id="c83f1-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-200">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="c83f1-201">長期的なサービスブランチ</span><span class="sxs-lookup"><span data-stu-id="c83f1-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="c83f1-202">✔️</span><span class="sxs-lookup"><span data-stu-id="c83f1-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="c83f1-203">以前のリリースノート</span><span class="sxs-lookup"><span data-stu-id="c83f1-203">Prior release notes</span></span>
* [<span data-ttu-id="c83f1-204">リリース ノート - 2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="c83f1-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="c83f1-205">リリース ノート - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="c83f1-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="c83f1-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="c83f1-206">See also</span></span>
* [<span data-ttu-id="c83f1-207">HoloLens の既知の問題</span><span class="sxs-lookup"><span data-stu-id="c83f1-207">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="c83f1-208">業務用機能</span><span class="sxs-lookup"><span data-stu-id="c83f1-208">Commercial features</span></span>](commercial-features.md)
* [<span data-ttu-id="c83f1-209">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="c83f1-209">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="c83f1-210">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="c83f1-210">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
