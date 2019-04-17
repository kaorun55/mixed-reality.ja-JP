---
title: 2016 年 8 月のリリース ノート
description: Windows 10 Anniversary リリース (2016 年秋) の HoloLens のリリース ノート
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リリース ノート、os、プラットフォーム、機能、商用のスイート
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603666"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="49841-104">2016 年 8 月のリリース ノート</span><span class="sxs-lookup"><span data-stu-id="49841-104">Release notes - August 2016</span></span>

<span data-ttu-id="49841-105">HoloLens チームは、開発者が取り組みの優先順位を Windows Insider Program からフィードバックをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="49841-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="49841-106">引き続き[フィードバックを提供](give-us-feedback.md)フィードバック ハブ経由、[デベロッパー フォーラム](https://forums.hololens.com)と[経由で Twitter @HoloLens ](https://twitter.com/hololens)。</span><span class="sxs-lookup"><span data-stu-id="49841-106">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="49841-107">Windows 10 Anniversary Update、HoloLens のチームが配信を支配はホログラフィック操作にさらに向上させます。</span><span class="sxs-lookup"><span data-stu-id="49841-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="49841-108">この更新で大規模な修正、改善、および企業と、Microsoft HoloLens Commercial Suite で使用可能な要求された概要の機能に注目します。</span><span class="sxs-lookup"><span data-stu-id="49841-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="49841-109">**最新リリース:** Windows Holographic の 2016 年 8 月の更新プログラム (**10.0.14393.0**、Windows 10 Anniversary リリース)</span><span class="sxs-lookup"><span data-stu-id="49841-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="49841-110">[現在のリリースに更新](updating-hololens.md)、オープン、*設定*に移動して、アプリ*更新とセキュリティ*を選択し、*更新プログラムの確認*ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="49841-110">To [update to the current release](updating-hololens.md), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="49841-111">新しい機能</span><span class="sxs-lookup"><span data-stu-id="49841-111">New features</span></span>

<span data-ttu-id="49841-112">**プロセスのデバッグにアタッチ**HoloLens はプロセスにアタッチ デバッグ サポートしているようになりました。</span><span class="sxs-lookup"><span data-stu-id="49841-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="49841-113">Visual Studio 2015 Update 3 を使用するには、HoloLens の実行中のアプリに接続して[デバッグを開始](using-visual-studio.md#debugging-an-installed-or-running-app)します。</span><span class="sxs-lookup"><span data-stu-id="49841-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](using-visual-studio.md#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="49841-114">これは、Visual Studio プロジェクトからデプロイする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="49841-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="49841-115">**HoloLens のエミュレーターを更新**HoloLens のエミュレーターの更新バージョンもリリースしました。</span><span class="sxs-lookup"><span data-stu-id="49841-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="49841-116">**Gamepad サポート**ペアリングし、HoloLens で Bluetooth ゲームパッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="49841-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="49841-117">新たにリリースされた Xbox のワイヤレス コント ローラー S は機能 Bluetooth 機能と、ゲームパッドが有効なお気に入りのゲームとアプリを再生するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="49841-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="49841-118">A[コント ローラーの更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)HoloLens と Xbox のワイヤレス コント ローラーの秒を接続する前に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49841-118">A [controller update](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="49841-119">Xbox のワイヤレス コント ローラーの S がでサポートされて[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)と[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。</span><span class="sxs-lookup"><span data-stu-id="49841-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="49841-120">Bluetooth コント ローラーの追加のモデルをアクセス、 [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。</span><span class="sxs-lookup"><span data-stu-id="49841-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="49841-121">機能強化と修正</span><span class="sxs-lookup"><span data-stu-id="49841-121">Improvements and fixes</span></span>

<span data-ttu-id="49841-122">Hololens の個々 の修正に加えてもから受信するすべての適合度プラットフォームの信頼性とパフォーマンスを向上させる Windows 更新プログラムがあるため、Windows 10 Anniversary update での残りの部分との同期が。</span><span class="sxs-lookup"><span data-stu-id="49841-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the Hololens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="49841-123">フィードバックは高い値し、リリースで修正プログラムの優先順位を設定します。</span><span class="sxs-lookup"><span data-stu-id="49841-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="49841-124">以下のエクスペリエンスを改善しました。</span><span class="sxs-lookup"><span data-stu-id="49841-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="49841-125">エクスペリエンスにログインします。</span><span class="sxs-lookup"><span data-stu-id="49841-125">log in experiences.</span></span>
* <span data-ttu-id="49841-126">社内参加します。</span><span class="sxs-lookup"><span data-stu-id="49841-126">workplace join.</span></span>
* <span data-ttu-id="49841-127">デバイスの電源の状態遷移の電力効率。</span><span class="sxs-lookup"><span data-stu-id="49841-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="49841-128">安定性 Mixed Reality をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="49841-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="49841-129">Bluetooth 接続の信頼性</span><span class="sxs-lookup"><span data-stu-id="49841-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="49841-130">マルチ アプリのシナリオでホログラム永続化します。</span><span class="sxs-lookup"><span data-stu-id="49841-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="49841-131">次の問題を修正しました。</span><span class="sxs-lookup"><span data-stu-id="49841-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="49841-132">Visual Studio プロファイラーとグラフィックス デバッガーの接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="49841-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="49841-133">写真とドキュメントは表示されません、デバイス ポータル ファイル エクスプ ローラー。</span><span class="sxs-lookup"><span data-stu-id="49841-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="49841-134">アプリ バーは、調整モードでは、上にカーソルが配置されるときに点滅します。</span><span class="sxs-lookup"><span data-stu-id="49841-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="49841-135">調整モードの場合、目注視ドット カーソルに変わります 4 矢印カーソルいずれかの時点より緩やかに変化します。</span><span class="sxs-lookup"><span data-stu-id="49841-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="49841-136">"こんにちは Cortana で音楽を再生"Groove は起動しません。</span><span class="sxs-lookup"><span data-stu-id="49841-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="49841-137">前回の更新後に"移動 Home"と答えるとが正しく表示されませんピン パネル。</span><span class="sxs-lookup"><span data-stu-id="49841-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="49841-138">Microsoft HoloLens の商用 Suite の概要</span><span class="sxs-lookup"><span data-stu-id="49841-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="49841-139">Microsoft HoloLens Commercial Suite エンタープライズ展開の準備ができました。</span><span class="sxs-lookup"><span data-stu-id="49841-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="49841-140">頻繁に要求されるいくつか追加しました[商用機能](commercial-features.md)早期のビジネス パートナーから。</span><span class="sxs-lookup"><span data-stu-id="49841-140">We've added several highly requested [commercial features](commercial-features.md) from our early business partners.</span></span>

<span data-ttu-id="49841-141">Microsoft HoloLens Commercial Suite を購入する、ローカルのマイクロソフト アカウント マネージャーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="49841-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="49841-142">キーの商用機能</span><span class="sxs-lookup"><span data-stu-id="49841-142">Key Commercial Features</span></span> 

* <span data-ttu-id="49841-143">**キオスク モード。**</span><span class="sxs-lookup"><span data-stu-id="49841-143">**Kiosk mode.**</span></span> <span data-ttu-id="49841-144">HoloLens のキオスク モードでは、デモまたはショーケースのエクスペリエンスを有効にするを実行するアプリを制限できます。</span><span class="sxs-lookup"><span data-stu-id="49841-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="49841-145">![キオスク モードでは、HoloLens は好みのアプリに直接起動します。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="49841-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="49841-146">**HoloLens のモバイル デバイス管理 (MDM)。**</span><span class="sxs-lookup"><span data-stu-id="49841-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="49841-147">IT 部門は、Microsoft Intune などのソリューションを使用して同時に複数の HoloLens デバイスを管理できます。</span><span class="sxs-lookup"><span data-stu-id="49841-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="49841-148">設定の管理、インストールするアプリの選択、組織のニーズに合わせたセキュリティ構成の設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="49841-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="49841-149">![HoloLens でモバイル デバイス管理は、複数のデバイスでのエンタープライズ グレードのデバイス管理を提供します。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="49841-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="49841-150">**Windows Update for Business。**</span><span class="sxs-lookup"><span data-stu-id="49841-150">**Windows Update for Business.**</span></span> <span data-ttu-id="49841-151">デバイスおよび long-term servicing branch のサポートにオペレーティング システムの更新プログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="49841-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="49841-152">**データのセキュリティ。**</span><span class="sxs-lookup"><span data-stu-id="49841-152">**Data security.**</span></span> <span data-ttu-id="49841-153">同じレベルの他の Windows デバイスのセキュリティ保護を提供する、HoloLens の BitLocker データ暗号化が有効です。</span><span class="sxs-lookup"><span data-stu-id="49841-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="49841-154">**職場のアクセス。**</span><span class="sxs-lookup"><span data-stu-id="49841-154">**Work access.**</span></span> <span data-ttu-id="49841-155">組織内のすべてのユーザーは、HoloLens で仮想プライベート ネットワーク経由で企業ネットワークにリモートで接続できます。</span><span class="sxs-lookup"><span data-stu-id="49841-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="49841-156">HoloLens の資格情報を必要とする Wi-fi ネットワークにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="49841-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="49841-157">**ビジネス向け Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="49841-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="49841-158">IT 部門はことができますも、特定 HoloLens 使用量、会社のアプリのみを格納しているエンタープライズ プライベート ストアの場合を設定します。</span><span class="sxs-lookup"><span data-stu-id="49841-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="49841-159">エンタープライズ ユーザーの選択したグループに、エンタープライズ ソフトウェアを安全に配信します。</span><span class="sxs-lookup"><span data-stu-id="49841-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="49841-160">開発エディションとCommercial Suite</span><span class="sxs-lookup"><span data-stu-id="49841-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="49841-161">機能</span><span class="sxs-lookup"><span data-stu-id="49841-161">Features</span></span></th><th><span data-ttu-id="49841-162">Development Edition</span><span class="sxs-lookup"><span data-stu-id="49841-162">Development Edition</span></span></th><th><span data-ttu-id="49841-163">Commercial Suite</span><span class="sxs-lookup"><span data-stu-id="49841-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="49841-164">デバイスの暗号化 (Bitlocker)</span><span class="sxs-lookup"><span data-stu-id="49841-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-165">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-166">仮想プライベート ネットワーク (VPN)</span><span class="sxs-lookup"><span data-stu-id="49841-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-167">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-168"><a href="using-the-windows-device-portal.md#kiosk-mode">キオスク モード</a></span><span class="sxs-lookup"><span data-stu-id="49841-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-169">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="49841-170">管理と展開</span><span class="sxs-lookup"><span data-stu-id="49841-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="49841-171">モバイル デバイス管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="49841-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="49841-172">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-173">登録解除をブロックする機能</span><span class="sxs-lookup"><span data-stu-id="49841-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-174">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-175">証明書ベースの企業の Wi-fi アクセス</span><span class="sxs-lookup"><span data-stu-id="49841-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-176">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-177">Microsoft Store (コンシューマー)</span><span class="sxs-lookup"><span data-stu-id="49841-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-178">コンシューマー</span><span class="sxs-lookup"><span data-stu-id="49841-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-179">MDM を介したフィルタ リング</span><span class="sxs-lookup"><span data-stu-id="49841-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">ビジネス ストア ポータル</a></span><span class="sxs-lookup"><span data-stu-id="49841-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-181">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="49841-182">セキュリティと ID</span><span class="sxs-lookup"><span data-stu-id="49841-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="49841-183">Azure Active Directory (AAD) でログイン</span><span class="sxs-lookup"><span data-stu-id="49841-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-184">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-185">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-186">Microsoft アカウント (MSA) でログイン</span><span class="sxs-lookup"><span data-stu-id="49841-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-187">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-188">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-189">暗証番号 (pin) と [次へ] の生成の資格情報のロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="49841-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-190">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-191">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">セキュア ブート</a></span><span class="sxs-lookup"><span data-stu-id="49841-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="49841-193">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-194">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="49841-195">サービスとサポート</span><span class="sxs-lookup"><span data-stu-id="49841-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="49841-196">システムの自動更新が到着します。</span><span class="sxs-lookup"><span data-stu-id="49841-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-197">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="49841-198">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span><span class="sxs-lookup"><span data-stu-id="49841-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-200">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="49841-201">長期的なサービス ブランチ</span><span class="sxs-lookup"><span data-stu-id="49841-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="49841-202">✔️</span><span class="sxs-lookup"><span data-stu-id="49841-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="49841-203">以前のリリース ノート</span><span class="sxs-lookup"><span data-stu-id="49841-203">Prior release notes</span></span>
* [<span data-ttu-id="49841-204">2016 年 5 月のリリース ノート</span><span class="sxs-lookup"><span data-stu-id="49841-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="49841-205">2016 年 3 月のリリース ノート</span><span class="sxs-lookup"><span data-stu-id="49841-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="49841-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="49841-206">See also</span></span>
* [<span data-ttu-id="49841-207">HoloLens の既知の問題</span><span class="sxs-lookup"><span data-stu-id="49841-207">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="49841-208">商用機能</span><span class="sxs-lookup"><span data-stu-id="49841-208">Commercial features</span></span>](commercial-features.md)
* [<span data-ttu-id="49841-209">ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="49841-209">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="49841-210">HoloLens のエミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="49841-210">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
