---
title: デバイスポータル API リファレンス
description: HoloLens の Windows デバイスポータルの API リファレンス
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows デバイスポータル、API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694430"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="1c146-104">デバイスポータル API リファレンス</span><span class="sxs-lookup"><span data-stu-id="1c146-104">Device portal API reference</span></span>

<span data-ttu-id="1c146-105">[Windows デバイスポータル](using-the-windows-device-portal.md)のすべての機能は REST API の上に構築されており、データにアクセスしたり、デバイスをプログラムで制御したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c146-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="1c146-106">アプリの撮る</span><span class="sxs-lookup"><span data-stu-id="1c146-106">App deloyment</span></span>

<span data-ttu-id="1c146-107">**/api/app/packagemanager/package (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="1c146-108">アプリをアンインストールします</span><span class="sxs-lookup"><span data-stu-id="1c146-108">Uninstalls an app</span></span>

<span data-ttu-id="1c146-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-109">Parameters</span></span>
* <span data-ttu-id="1c146-110">パックアンインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="1c146-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="1c146-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="1c146-112">アプリをインストールします</span><span class="sxs-lookup"><span data-stu-id="1c146-112">Installs an App</span></span>

<span data-ttu-id="1c146-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-113">Parameters</span></span>
* <span data-ttu-id="1c146-114">パックインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="1c146-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="1c146-115">ペイロード</span><span class="sxs-lookup"><span data-stu-id="1c146-115">Payload</span></span>
* <span data-ttu-id="1c146-116">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="1c146-116">multi-part conforming http body</span></span>

<span data-ttu-id="1c146-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="1c146-118">システムにインストールされているアプリの一覧を詳細と共に取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="1c146-119">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-119">Return data</span></span>
* <span data-ttu-id="1c146-120">インストールされているパッケージの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="1c146-120">List of installed packages with details</span></span>

<span data-ttu-id="1c146-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="1c146-122">進行中のアプリのインストールの状態を取得します</span><span class="sxs-lookup"><span data-stu-id="1c146-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="1c146-123">ダンプの収集</span><span class="sxs-lookup"><span data-stu-id="1c146-123">Dump collection</span></span>

<span data-ttu-id="1c146-124">**/api/debug/dump/usermode/crashcontrol (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="1c146-125">サイドロードアプリのクラッシュダンプの収集を無効にします。</span><span class="sxs-lookup"><span data-stu-id="1c146-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="1c146-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-126">Parameters</span></span>
* <span data-ttu-id="1c146-127">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="1c146-127">packageFullname : package name</span></span>

<span data-ttu-id="1c146-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="1c146-129">サイドロード apps のクラッシュダンプの収集の設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="1c146-130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-130">Parameters</span></span>
* <span data-ttu-id="1c146-131">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="1c146-131">packageFullname : package name</span></span>

<span data-ttu-id="1c146-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="1c146-133">サイドロードアプリのダンプ制御設定を有効にして設定します</span><span class="sxs-lookup"><span data-stu-id="1c146-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="1c146-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-134">Parameters</span></span>
* <span data-ttu-id="1c146-135">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="1c146-135">packageFullname : package name</span></span>

<span data-ttu-id="1c146-136">**/api/debug/dump/usermode/crashdump (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="1c146-137">サイドロードアプリのクラッシュダンプを削除します。</span><span class="sxs-lookup"><span data-stu-id="1c146-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1c146-138">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-138">Parameters</span></span>
* <span data-ttu-id="1c146-139">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="1c146-139">packageFullname : package name</span></span>
* <span data-ttu-id="1c146-140">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="1c146-140">fileName : dump file name</span></span>

<span data-ttu-id="1c146-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="1c146-142">サイドロードアプリのクラッシュダンプを取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1c146-143">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-143">Parameters</span></span>
* <span data-ttu-id="1c146-144">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="1c146-144">packageFullname : package name</span></span>
* <span data-ttu-id="1c146-145">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="1c146-145">fileName : dump file name</span></span>

<span data-ttu-id="1c146-146">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-146">Return data</span></span>
* <span data-ttu-id="1c146-147">ダンプファイル。</span><span class="sxs-lookup"><span data-stu-id="1c146-147">Dump file.</span></span> <span data-ttu-id="1c146-148">WinDbg または Visual Studio を使用して検査する</span><span class="sxs-lookup"><span data-stu-id="1c146-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="1c146-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="1c146-150">サイドロードアプリのすべてのクラッシュダンプの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="1c146-151">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-151">Return data</span></span>
* <span data-ttu-id="1c146-152">サイドロードされたアプリごとのクラッシュダンプの一覧</span><span class="sxs-lookup"><span data-stu-id="1c146-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="1c146-153">ETW</span><span class="sxs-lookup"><span data-stu-id="1c146-153">ETW</span></span>

<span data-ttu-id="1c146-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="1c146-155">登録されたプロバイダーを列挙します</span><span class="sxs-lookup"><span data-stu-id="1c146-155">Enumerates registered providers</span></span>

<span data-ttu-id="1c146-156">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-156">Return data</span></span>
* <span data-ttu-id="1c146-157">プロバイダー、フレンドリ名、GUID の一覧</span><span class="sxs-lookup"><span data-stu-id="1c146-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="1c146-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1c146-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="1c146-159">リアルタイム ETW セッションを作成します。websocket 経由で管理されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="1c146-160">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-160">Return data</span></span>
* <span data-ttu-id="1c146-161">有効なプロバイダーからの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="1c146-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="1c146-162">ホログラフィック OS</span><span class="sxs-lookup"><span data-stu-id="1c146-162">Holographic OS</span></span>

<span data-ttu-id="1c146-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="1c146-164">システムに登録されていない HoloLens 固有の ETW プロバイダーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="1c146-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="1c146-166">実行中のすべてのサービスの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-166">Returns the states of all services running.</span></span>

<span data-ttu-id="1c146-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="1c146-168">格納されている IPD (Interpupillary distance) をミリメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="1c146-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="1c146-170">IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-170">Sets the IPD</span></span>

<span data-ttu-id="1c146-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-171">Parameters</span></span>
* <span data-ttu-id="1c146-172">ipdミリメートル単位で設定する新しい IPD 値</span><span class="sxs-lookup"><span data-stu-id="1c146-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="1c146-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="1c146-174">Device Portal の HTTPS 要件を取得する</span><span class="sxs-lookup"><span data-stu-id="1c146-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1c146-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="1c146-176">デバイスポータルの HTTPS 要件を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1c146-177">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-177">Parameters</span></span>
* <span data-ttu-id="1c146-178">必須: はい、いいえ、または既定値</span><span class="sxs-lookup"><span data-stu-id="1c146-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="1c146-179">Holographic の認識</span><span class="sxs-lookup"><span data-stu-id="1c146-179">Holographic Perception</span></span>

<span data-ttu-id="1c146-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1c146-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="1c146-181">Websocket のアップグレードを受け入れ、30 fps で更新を送信する認識クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c146-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="1c146-182">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-182">Parameters</span></span>
* <span data-ttu-id="1c146-183">clientmode: "active" は、受動的に確立できないときにビジュアル追跡モードを強制します。</span><span class="sxs-lookup"><span data-stu-id="1c146-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="1c146-184">Holographic Thermal</span><span class="sxs-lookup"><span data-stu-id="1c146-184">Holographic Thermal</span></span>

<span data-ttu-id="1c146-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="1c146-186">デバイスの温度ステージを取得する (通常は0、1ウォーム、2重大)</span><span class="sxs-lookup"><span data-stu-id="1c146-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="1c146-187">認識シミュレーションの制御</span><span class="sxs-lookup"><span data-stu-id="1c146-187">Perception Simulation Control</span></span>

<span data-ttu-id="1c146-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="1c146-189">シミュレーションモードを取得する</span><span class="sxs-lookup"><span data-stu-id="1c146-189">Get the simulation mode</span></span>

<span data-ttu-id="1c146-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="1c146-191">シミュレーションモードの設定</span><span class="sxs-lookup"><span data-stu-id="1c146-191">Set the simulation mode</span></span>

<span data-ttu-id="1c146-192">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-192">Parameters</span></span>
* <span data-ttu-id="1c146-193">モード: シミュレーションモード: 既定、シミュレーション、リモート、レガシ</span><span class="sxs-lookup"><span data-stu-id="1c146-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="1c146-194">**/api/holographic/simulation/control/stream (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="1c146-195">コントロールストリームを削除します。</span><span class="sxs-lookup"><span data-stu-id="1c146-195">Delete a control stream.</span></span>

<span data-ttu-id="1c146-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1c146-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="1c146-197">コントロールストリームの web ソケット接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="1c146-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="1c146-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="1c146-199">コントロールストリームを作成するか (優先順位が必要)、作成されたストリームにデータを post します (streamId が必要)。</span><span class="sxs-lookup"><span data-stu-id="1c146-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="1c146-200">ポストされたデータは ' application/オクテット-stream ' 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c146-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="1c146-201">認識シミュレーションの再生</span><span class="sxs-lookup"><span data-stu-id="1c146-201">Perception Simulation Playback</span></span>

<span data-ttu-id="1c146-202">**/api/holographic/simulation/playback/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="1c146-203">記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="1c146-203">Delete a recording.</span></span>

<span data-ttu-id="1c146-204">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-204">Parameters</span></span>
* <span data-ttu-id="1c146-205">録音削除する記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="1c146-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="1c146-207">記録をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="1c146-207">Upload a recording.</span></span>

<span data-ttu-id="1c146-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="1c146-209">すべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-209">Get all recordings.</span></span>

<span data-ttu-id="1c146-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="1c146-211">記録の現在の再生状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="1c146-212">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-212">Parameters</span></span>
* <span data-ttu-id="1c146-213">録音記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-213">recording : Name of recording.</span></span>

<span data-ttu-id="1c146-214">**/api/holographic/simulation/playback/session/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="1c146-215">記録をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="1c146-215">Unload a recording.</span></span>

<span data-ttu-id="1c146-216">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-216">Parameters</span></span>
* <span data-ttu-id="1c146-217">録音アンロードする記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="1c146-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="1c146-219">記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1c146-219">Load a recording.</span></span>

<span data-ttu-id="1c146-220">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-220">Parameters</span></span>
* <span data-ttu-id="1c146-221">録音読み込む記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="1c146-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="1c146-223">読み込まれたすべての録音を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-223">Get all loaded recordings.</span></span>

<span data-ttu-id="1c146-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="1c146-225">記録を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="1c146-225">Pause a recording.</span></span>

<span data-ttu-id="1c146-226">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-226">Parameters</span></span>
* <span data-ttu-id="1c146-227">録音記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-227">recording : Name of recording.</span></span>

<span data-ttu-id="1c146-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="1c146-229">録音を再生します。</span><span class="sxs-lookup"><span data-stu-id="1c146-229">Play a recording.</span></span>

<span data-ttu-id="1c146-230">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-230">Parameters</span></span>
* <span data-ttu-id="1c146-231">録音記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-231">recording : Name of recording.</span></span>

<span data-ttu-id="1c146-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="1c146-233">記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="1c146-233">Stop a recording.</span></span>

<span data-ttu-id="1c146-234">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-234">Parameters</span></span>
* <span data-ttu-id="1c146-235">録音記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-235">recording : Name of recording.</span></span>

<span data-ttu-id="1c146-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="1c146-237">読み込まれた記録のデータの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="1c146-238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-238">Parameters</span></span>
* <span data-ttu-id="1c146-239">録音記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="1c146-240">認識のシミュレーション記録</span><span class="sxs-lookup"><span data-stu-id="1c146-240">Perception Simulation Recording</span></span>

<span data-ttu-id="1c146-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="1c146-242">記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="1c146-242">Start a recording.</span></span> <span data-ttu-id="1c146-243">一度にアクティブにできる記録は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="1c146-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="1c146-244">ヘッド、ハンド、spatialMapping、または環境のいずれかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c146-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="1c146-245">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-245">Parameters</span></span>
* <span data-ttu-id="1c146-246">矢印ヘッドデータを記録するには、を1に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="1c146-247">みるハンドデータを記録するには、を1に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="1c146-248">spatialMapping :空間マッピングを記録するには、1に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="1c146-249">environment環境データを記録するには、を1に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="1c146-250">指定記録の名前。</span><span class="sxs-lookup"><span data-stu-id="1c146-250">name : Name of the recording.</span></span>
* <span data-ttu-id="1c146-251">singleSpatialMappingFrame :1に設定すると、空間マッピングフレームが1つだけ記録されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="1c146-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="1c146-253">記録の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-253">Get recording state.</span></span>

<span data-ttu-id="1c146-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="1c146-255">現在の記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="1c146-255">Stop the current recording.</span></span> <span data-ttu-id="1c146-256">記録はファイルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="1c146-257">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="1c146-257">Mixed Reality Capture</span></span>

<span data-ttu-id="1c146-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="1c146-259">混合の現実ファイルをデバイスからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1c146-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="1c146-260">ストリーミングには op = stream クエリパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c146-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="1c146-261">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-261">Parameters</span></span>
* <span data-ttu-id="1c146-262">/db取得するビデオファイルの名前 (hex64 encoded)</span><span class="sxs-lookup"><span data-stu-id="1c146-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="1c146-263">op: ストリーム</span><span class="sxs-lookup"><span data-stu-id="1c146-263">op : stream</span></span>

<span data-ttu-id="1c146-264">**/api/holographic/mrc/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="1c146-265">デバイスから mixed reality の記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="1c146-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="1c146-266">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-266">Parameters</span></span>
* <span data-ttu-id="1c146-267">/db削除するファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="1c146-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="1c146-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="1c146-269">デバイスに格納されている mixed reality ファイルの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="1c146-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="1c146-271">Mixed reality の写真を取得し、デバイスにファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1c146-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="1c146-272">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-272">Parameters</span></span>
* <span data-ttu-id="1c146-273">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-274">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-275">RenderFromCamera:(HoloLens 2 のみ) 写真/ビデオカメラの視点からレンダー: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="1c146-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="1c146-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="1c146-277">既定の mixed reality キャプチャ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="1c146-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="1c146-279">既定の mixed reality キャプチャ設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c146-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="1c146-280">これらの設定の一部は、システムの MRC の写真とビデオキャプチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="1c146-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="1c146-282">記録された mixed reality の状態を取得します (実行中、停止済み)</span><span class="sxs-lookup"><span data-stu-id="1c146-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="1c146-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="1c146-284">指定したファイルのサムネイルイメージを取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="1c146-285">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-285">Parameters</span></span>
* <span data-ttu-id="1c146-286">/dbサムネイルが要求されているファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="1c146-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="1c146-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="1c146-288">Mixed reality の記録を開始します</span><span class="sxs-lookup"><span data-stu-id="1c146-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="1c146-289">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-289">Parameters</span></span>
* <span data-ttu-id="1c146-290">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-291">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-292">mic: キャプチャマイク: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-293">ループバック: キャプチャアプリオーディオ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-294">RenderFromCamera:(HoloLens 2 のみ) 写真/ビデオカメラの視点からレンダー: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="1c146-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="1c146-295">vstab :(HoloLens 2 のみ) ビデオ安定化を有効にします (true または false) (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="1c146-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="1c146-296">vstabbuffer:(HoloLens 2 のみ) ビデオ安定化バッファー待機時間:0 ~ 30 フレーム (既定値は15フレーム)</span><span class="sxs-lookup"><span data-stu-id="1c146-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="1c146-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="1c146-298">現在の mixed reality 記録を停止します</span><span class="sxs-lookup"><span data-stu-id="1c146-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="1c146-299">Mixed Reality ストリーミング</span><span class="sxs-lookup"><span data-stu-id="1c146-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="1c146-300">HoloLens は、フラグメント化された mp4 のチャンクダウンロードを使用して、混合現実のライブプレビューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1c146-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="1c146-301">混合現実のストリームは、キャプチャ対象を制御するために、同じパラメーターのセットを共有します。</span><span class="sxs-lookup"><span data-stu-id="1c146-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="1c146-302">holo: キャプチャホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="1c146-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1c146-303">pv: キャプチャの PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="1c146-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1c146-304">mic: マイクのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="1c146-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1c146-305">ループバック: アプリオーディオのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="1c146-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1c146-306">これらのいずれも指定されていない場合、ホログラム、photo/video カメラ、アプリオーディオがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="1c146-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="1c146-307">指定されている場合: 未指定のパラメーターは既定で false に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="1c146-308">省略可能なパラメーター (HoloLens 2 のみ)</span><span class="sxs-lookup"><span data-stu-id="1c146-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="1c146-309">RenderFromCamera: 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="1c146-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="1c146-310">vstab: ビデオ安定化を有効にします。 true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="1c146-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="1c146-311">vstabbuffer: ビデオ安定化バッファーの待機時間:0 ~ 30 フレーム (既定値は15フレーム)</span><span class="sxs-lookup"><span data-stu-id="1c146-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="1c146-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="1c146-313">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="1c146-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="1c146-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="1c146-315">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="1c146-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="1c146-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="1c146-317">854x480p 30 fps 2.5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="1c146-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="1c146-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="1c146-319">428x240p 15fps 0.6 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="1c146-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="1c146-320">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1c146-320">Networking</span></span>

<span data-ttu-id="1c146-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="1c146-322">現在の ip 構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="1c146-323">OS 情報</span><span class="sxs-lookup"><span data-stu-id="1c146-323">OS Information</span></span>

<span data-ttu-id="1c146-324">**/api/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="1c146-325">オペレーティングシステム情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-325">Gets operating system information</span></span>

<span data-ttu-id="1c146-326">**/api/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="1c146-327">コンピューター名を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-327">Gets the machine name</span></span>

<span data-ttu-id="1c146-328">**/api/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="1c146-329">コンピューター名を設定します</span><span class="sxs-lookup"><span data-stu-id="1c146-329">Sets the machine name</span></span>

<span data-ttu-id="1c146-330">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-330">Parameters</span></span>
* <span data-ttu-id="1c146-331">指定に設定する新しいコンピューター名 (hex64 encoded)</span><span class="sxs-lookup"><span data-stu-id="1c146-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="1c146-332">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="1c146-332">Performance data</span></span>

<span data-ttu-id="1c146-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="1c146-334">詳細を含む実行中のプロセスの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="1c146-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="1c146-335">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-335">Return data</span></span>
* <span data-ttu-id="1c146-336">各プロセスのプロセスと詳細の一覧を含む JSON</span><span class="sxs-lookup"><span data-stu-id="1c146-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="1c146-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="1c146-338">システムパフォーマンス統計情報 (i/o 読み取り/書き込み、メモリ統計など) を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="1c146-339">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-339">Return data</span></span>
* <span data-ttu-id="1c146-340">システム情報を含む JSON:CPU、GPU、メモリ、ネットワーク、IO</span><span class="sxs-lookup"><span data-stu-id="1c146-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="1c146-341">Power</span><span class="sxs-lookup"><span data-stu-id="1c146-341">Power</span></span>

<span data-ttu-id="1c146-342">**/api/バッテリ (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="1c146-343">現在のバッテリの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-343">Gets the current battery state</span></span>

<span data-ttu-id="1c146-344">**//(GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="1c146-345">システムが低電力状態であるかどうかを確認します</span><span class="sxs-lookup"><span data-stu-id="1c146-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="1c146-346">リモート コントロール</span><span class="sxs-lookup"><span data-stu-id="1c146-346">Remote Control</span></span>

<span data-ttu-id="1c146-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="1c146-348">ターゲットデバイスを再起動します</span><span class="sxs-lookup"><span data-stu-id="1c146-348">Restarts the target device</span></span>

<span data-ttu-id="1c146-349">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="1c146-350">ターゲットデバイスをシャットダウンします</span><span class="sxs-lookup"><span data-stu-id="1c146-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="1c146-351">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="1c146-351">Task Manager</span></span>

<span data-ttu-id="1c146-352">**/api/taskmanager/app (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="1c146-353">モダンアプリを停止します</span><span class="sxs-lookup"><span data-stu-id="1c146-353">Stops a modern app</span></span>

<span data-ttu-id="1c146-354">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-354">Parameters</span></span>
* <span data-ttu-id="1c146-355">パックアプリケーションパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="1c146-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="1c146-356">forcestop:すべてのプロセスを強制的に停止する (= yes)</span><span class="sxs-lookup"><span data-stu-id="1c146-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="1c146-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="1c146-358">モダンアプリを開始します</span><span class="sxs-lookup"><span data-stu-id="1c146-358">Starts a modern app</span></span>

<span data-ttu-id="1c146-359">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-359">Parameters</span></span>
* <span data-ttu-id="1c146-360">appidアプリの開始、hex64 エンコード</span><span class="sxs-lookup"><span data-stu-id="1c146-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="1c146-361">パックアプリケーションパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="1c146-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="1c146-362">WiFi の管理</span><span class="sxs-lookup"><span data-stu-id="1c146-362">WiFi Management</span></span>

<span data-ttu-id="1c146-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="1c146-364">ワイヤレスネットワークインターフェイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="1c146-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="1c146-365">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-365">Return data</span></span>
* <span data-ttu-id="1c146-366">詳細 (GUID、説明など) があるワイヤレスインターフェイスの一覧</span><span class="sxs-lookup"><span data-stu-id="1c146-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="1c146-367">**/api/wifi/network (削除)**</span><span class="sxs-lookup"><span data-stu-id="1c146-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="1c146-368">指定したインターフェイスのネットワークに関連付けられているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="1c146-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="1c146-369">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-369">Parameters</span></span>
* <span data-ttu-id="1c146-370">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="1c146-370">interface : network interface guid</span></span>
* <span data-ttu-id="1c146-371">プロファイル: プロファイル名</span><span class="sxs-lookup"><span data-stu-id="1c146-371">profile : profile name</span></span>

<span data-ttu-id="1c146-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="1c146-373">指定されたネットワークインターフェイスのワイヤレスネットワークを列挙します</span><span class="sxs-lookup"><span data-stu-id="1c146-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="1c146-374">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-374">Parameters</span></span>
* <span data-ttu-id="1c146-375">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="1c146-375">interface : network interface guid</span></span>

<span data-ttu-id="1c146-376">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-376">Return data</span></span>
* <span data-ttu-id="1c146-377">ネットワークインターフェイスで検出されたワイヤレスネットワークの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="1c146-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="1c146-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="1c146-379">指定されたインターフェイスでネットワークに接続または切断します。</span><span class="sxs-lookup"><span data-stu-id="1c146-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="1c146-380">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-380">Parameters</span></span>
* <span data-ttu-id="1c146-381">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="1c146-381">interface : network interface guid</span></span>
* <span data-ttu-id="1c146-382">ssid: 接続先の ssid、hex64 encoded、</span><span class="sxs-lookup"><span data-stu-id="1c146-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="1c146-383">op: 接続または切断</span><span class="sxs-lookup"><span data-stu-id="1c146-383">op : connect or disconnect</span></span>
* <span data-ttu-id="1c146-384">createprofile: はいまたはいいえ</span><span class="sxs-lookup"><span data-stu-id="1c146-384">createprofile : yes or no</span></span>
* <span data-ttu-id="1c146-385">キー: shared key、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="1c146-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="1c146-386">Windows パフォーマンス レコーダー</span><span class="sxs-lookup"><span data-stu-id="1c146-386">Windows Performance Recorder</span></span>

<span data-ttu-id="1c146-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="1c146-388">WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="1c146-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="1c146-389">ペイロード</span><span class="sxs-lookup"><span data-stu-id="1c146-389">Payload</span></span>
* <span data-ttu-id="1c146-390">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="1c146-390">multi-part conforming http body</span></span>

<span data-ttu-id="1c146-391">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-391">Return data</span></span>
* <span data-ttu-id="1c146-392">WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-392">Returns the WPR session status.</span></span>

<span data-ttu-id="1c146-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="1c146-394">WPR セッションの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c146-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="1c146-395">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-395">Return data</span></span>
* <span data-ttu-id="1c146-396">WPR セッションの状態。</span><span class="sxs-lookup"><span data-stu-id="1c146-396">WPR session status.</span></span>

<span data-ttu-id="1c146-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="1c146-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="1c146-398">WPR (パフォーマンス) トレースセッションを停止します</span><span class="sxs-lookup"><span data-stu-id="1c146-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="1c146-399">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-399">Return data</span></span>
* <span data-ttu-id="1c146-400">トレース ETL ファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-400">Returns the trace ETL file</span></span>

<span data-ttu-id="1c146-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1c146-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="1c146-402">WPR (パフォーマンス) トレースセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="1c146-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="1c146-403">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c146-403">Parameters</span></span>
* <span data-ttu-id="1c146-404">profileプロファイル名。</span><span class="sxs-lookup"><span data-stu-id="1c146-404">profile : Profile name.</span></span> <span data-ttu-id="1c146-405">使用可能なプロファイルは perfprofiles/profiles. json に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c146-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="1c146-406">データを返す</span><span class="sxs-lookup"><span data-stu-id="1c146-406">Return data</span></span>
* <span data-ttu-id="1c146-407">開始時に、WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="1c146-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c146-408">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c146-408">See also</span></span>
* [<span data-ttu-id="1c146-409">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="1c146-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="1c146-410">デバイスポータルコア API リファレンス (UWP)</span><span class="sxs-lookup"><span data-stu-id="1c146-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
