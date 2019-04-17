---
title: デバイス ポータル API リファレンス
description: HoloLens で Windows Device Portal の API リファレンス
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows Device Portal の API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603277"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="0a4eb-104">デバイス ポータル API リファレンス</span><span class="sxs-lookup"><span data-stu-id="0a4eb-104">Device portal API reference</span></span>

<span data-ttu-id="0a4eb-105">内のすべて、 [Windows Device Portal](using-the-windows-device-portal.md)データにアクセスし、デバイスの管理をプログラム的に使用できる REST API の上に構築されます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="0a4eb-106">アプリの展開</span><span class="sxs-lookup"><span data-stu-id="0a4eb-106">App deloyment</span></span>

<span data-ttu-id="0a4eb-107">**/api/app/packagemanager/package (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="0a4eb-108">アプリをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-108">Uninstalls an app</span></span>

<span data-ttu-id="0a4eb-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-109">Parameters</span></span>
* <span data-ttu-id="0a4eb-110">パッケージ:アンインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="0a4eb-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="0a4eb-112">アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-112">Installs an App</span></span>

<span data-ttu-id="0a4eb-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-113">Parameters</span></span>
* <span data-ttu-id="0a4eb-114">パッケージ:パッケージをインストールするのファイル名。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="0a4eb-115">ペイロード</span><span class="sxs-lookup"><span data-stu-id="0a4eb-115">Payload</span></span>
* <span data-ttu-id="0a4eb-116">準拠したマルチパートの http 本文</span><span class="sxs-lookup"><span data-stu-id="0a4eb-116">multi-part conforming http body</span></span>

<span data-ttu-id="0a4eb-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="0a4eb-118">詳細と、システムにインストールされているアプリの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="0a4eb-119">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-119">Return data</span></span>
* <span data-ttu-id="0a4eb-120">詳細とインストールされているパッケージの一覧</span><span class="sxs-lookup"><span data-stu-id="0a4eb-120">List of installed packages with details</span></span>

<span data-ttu-id="0a4eb-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="0a4eb-122">アプリのインストールの進行状況での状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="0a4eb-123">ダンプの収集</span><span class="sxs-lookup"><span data-stu-id="0a4eb-123">Dump collection</span></span>

<span data-ttu-id="0a4eb-124">**/api/debug/dump/usermode/crashcontrol (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="0a4eb-125">サイドロードされたアプリのダンプの収集がクラッシュする無効にします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="0a4eb-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-126">Parameters</span></span>
* <span data-ttu-id="0a4eb-127">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-127">packageFullname : package name</span></span>

<span data-ttu-id="0a4eb-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="0a4eb-129">クラッシュ ダンプの収集にサイドロードしたアプリの設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="0a4eb-130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-130">Parameters</span></span>
* <span data-ttu-id="0a4eb-131">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-131">packageFullname : package name</span></span>

<span data-ttu-id="0a4eb-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="0a4eb-133">有効にし、サイドロードされたアプリのダンプ制御の設定の設定</span><span class="sxs-lookup"><span data-stu-id="0a4eb-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="0a4eb-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-134">Parameters</span></span>
* <span data-ttu-id="0a4eb-135">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-135">packageFullname : package name</span></span>

<span data-ttu-id="0a4eb-136">**/api/debug/dump/usermode/crashdump (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="0a4eb-137">サイドロードされたアプリのクラッシュ ダンプを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="0a4eb-138">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-138">Parameters</span></span>
* <span data-ttu-id="0a4eb-139">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-139">packageFullname : package name</span></span>
* <span data-ttu-id="0a4eb-140">ファイル名: ダンプ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="0a4eb-140">fileName : dump file name</span></span>

<span data-ttu-id="0a4eb-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="0a4eb-142">サイドロードされたアプリのクラッシュ ダンプを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="0a4eb-143">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-143">Parameters</span></span>
* <span data-ttu-id="0a4eb-144">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-144">packageFullname : package name</span></span>
* <span data-ttu-id="0a4eb-145">ファイル名: ダンプ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="0a4eb-145">fileName : dump file name</span></span>

<span data-ttu-id="0a4eb-146">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-146">Return data</span></span>
* <span data-ttu-id="0a4eb-147">ダンプ ファイル。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-147">Dump file.</span></span> <span data-ttu-id="0a4eb-148">WinDbg または Visual Studio での検査します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="0a4eb-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="0a4eb-150">サイドロードしたアプリのすべてのクラッシュ ダンプのリストを返します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="0a4eb-151">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-151">Return data</span></span>
* <span data-ttu-id="0a4eb-152">サイド ロード アプリごとの一連のクラッシュ ダンプします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="0a4eb-153">ETW</span><span class="sxs-lookup"><span data-stu-id="0a4eb-153">ETW</span></span>

<span data-ttu-id="0a4eb-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="0a4eb-155">登録されているプロバイダーを列挙します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-155">Enumerates registered providers</span></span>

<span data-ttu-id="0a4eb-156">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-156">Return data</span></span>
* <span data-ttu-id="0a4eb-157">プロバイダー、フレンドリ名と GUID の一覧</span><span class="sxs-lookup"><span data-stu-id="0a4eb-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="0a4eb-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="0a4eb-159">リアルタイムの ETW セッションを作成します。websocket 経由で管理します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="0a4eb-160">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-160">Return data</span></span>
* <span data-ttu-id="0a4eb-161">有効なプロバイダーから ETW イベント</span><span class="sxs-lookup"><span data-stu-id="0a4eb-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="0a4eb-162">ホログラフィック OS</span><span class="sxs-lookup"><span data-stu-id="0a4eb-162">Holographic OS</span></span>

<span data-ttu-id="0a4eb-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="0a4eb-164">システムに登録されていない HoloLens 特定 ETW プロバイダーの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="0a4eb-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="0a4eb-166">実行されているすべてのサービスの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-166">Returns the states of all services running.</span></span>

<span data-ttu-id="0a4eb-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="0a4eb-168">ミリメートル単位ストアド IPD (Interpupillary 距離) を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="0a4eb-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="0a4eb-170">IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-170">Sets the IPD</span></span>

<span data-ttu-id="0a4eb-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-171">Parameters</span></span>
* <span data-ttu-id="0a4eb-172">ipd:ミリメートル単位で設定される新しい IPD 値</span><span class="sxs-lookup"><span data-stu-id="0a4eb-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="0a4eb-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="0a4eb-174">Device Portal の HTTPS 要件を取得する</span><span class="sxs-lookup"><span data-stu-id="0a4eb-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="0a4eb-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="0a4eb-176">デバイスのポータルの HTTPS 要件を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="0a4eb-177">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-177">Parameters</span></span>
* <span data-ttu-id="0a4eb-178">必須: yes、no または既定値</span><span class="sxs-lookup"><span data-stu-id="0a4eb-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="0a4eb-179">Holographic Perception</span><span class="sxs-lookup"><span data-stu-id="0a4eb-179">Holographic Perception</span></span>

<span data-ttu-id="0a4eb-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="0a4eb-181">Websocket のアップグレードを受け取り、30 fps で更新プログラムを送信する perception クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="0a4eb-182">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-182">Parameters</span></span>
* <span data-ttu-id="0a4eb-183">clientmode:"active"強制的 visual 追跡モード受動的に確立されることはできません</span><span class="sxs-lookup"><span data-stu-id="0a4eb-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="0a4eb-184">Holographic 温度</span><span class="sxs-lookup"><span data-stu-id="0a4eb-184">Holographic Thermal</span></span>

<span data-ttu-id="0a4eb-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="0a4eb-186">(通常 0、1 ウォーム、重要な 2) のデバイスの温度のステージを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="0a4eb-187">Perception シミュレーション コントロール</span><span class="sxs-lookup"><span data-stu-id="0a4eb-187">Perception Simulation Control</span></span>

<span data-ttu-id="0a4eb-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="0a4eb-189">シミュレーションのモードを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-189">Get the simulation mode</span></span>

<span data-ttu-id="0a4eb-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="0a4eb-191">シミュレーションのモードを設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-191">Set the simulation mode</span></span>

<span data-ttu-id="0a4eb-192">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-192">Parameters</span></span>
* <span data-ttu-id="0a4eb-193">モード: シミュレーション モード: 既定では、シミュレーション、リモートのレガシ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="0a4eb-194">**/api/holographic/simulation/control/stream (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="0a4eb-195">コントロールのストリームを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-195">Delete a control stream.</span></span>

<span data-ttu-id="0a4eb-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="0a4eb-197">コントロールのストリームの web ソケット接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="0a4eb-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="0a4eb-199">コントロールのストリームを作成する (優先度が必要) または作成されたストリーム (必要な streamId) にデータをポストします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="0a4eb-200">ポストされたデータは、' アプリケーションまたはオクテット ストリーム ' 型のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="0a4eb-201">Perception シミュレーションの再生</span><span class="sxs-lookup"><span data-stu-id="0a4eb-201">Perception Simulation Playback</span></span>

<span data-ttu-id="0a4eb-202">**/api/holographic/simulation/playback/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="0a4eb-203">録画を削除します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-203">Delete a recording.</span></span>

<span data-ttu-id="0a4eb-204">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-204">Parameters</span></span>
* <span data-ttu-id="0a4eb-205">録音:削除する記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="0a4eb-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="0a4eb-207">録画をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-207">Upload a recording.</span></span>

<span data-ttu-id="0a4eb-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="0a4eb-209">すべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-209">Get all recordings.</span></span>

<span data-ttu-id="0a4eb-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="0a4eb-211">録画の現在の再生状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="0a4eb-212">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-212">Parameters</span></span>
* <span data-ttu-id="0a4eb-213">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-213">recording : Name of recording.</span></span>

<span data-ttu-id="0a4eb-214">**/api/holographic/simulation/playback/session/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="0a4eb-215">録画をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-215">Unload a recording.</span></span>

<span data-ttu-id="0a4eb-216">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-216">Parameters</span></span>
* <span data-ttu-id="0a4eb-217">録音:アンロードする記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="0a4eb-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="0a4eb-219">録画を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-219">Load a recording.</span></span>

<span data-ttu-id="0a4eb-220">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-220">Parameters</span></span>
* <span data-ttu-id="0a4eb-221">録音:記録を読み込むの名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="0a4eb-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="0a4eb-223">読み込まれたすべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-223">Get all loaded recordings.</span></span>

<span data-ttu-id="0a4eb-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="0a4eb-225">記録を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-225">Pause a recording.</span></span>

<span data-ttu-id="0a4eb-226">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-226">Parameters</span></span>
* <span data-ttu-id="0a4eb-227">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-227">recording : Name of recording.</span></span>

<span data-ttu-id="0a4eb-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="0a4eb-229">記録を再生します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-229">Play a recording.</span></span>

<span data-ttu-id="0a4eb-230">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-230">Parameters</span></span>
* <span data-ttu-id="0a4eb-231">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-231">recording : Name of recording.</span></span>

<span data-ttu-id="0a4eb-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="0a4eb-233">録画を停止します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-233">Stop a recording.</span></span>

<span data-ttu-id="0a4eb-234">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-234">Parameters</span></span>
* <span data-ttu-id="0a4eb-235">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-235">recording : Name of recording.</span></span>

<span data-ttu-id="0a4eb-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="0a4eb-237">読み込まれた記録では、データの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="0a4eb-238">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-238">Parameters</span></span>
* <span data-ttu-id="0a4eb-239">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="0a4eb-240">Perception シミュレーションの記録</span><span class="sxs-lookup"><span data-stu-id="0a4eb-240">Perception Simulation Recording</span></span>

<span data-ttu-id="0a4eb-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="0a4eb-242">録画を開始します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-242">Start a recording.</span></span> <span data-ttu-id="0a4eb-243">1 つの記録のみを一度にアクティブにできます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="0a4eb-244">Head、手、spatialMapping または環境のいずれかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="0a4eb-245">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-245">Parameters</span></span>
* <span data-ttu-id="0a4eb-246">ヘッド:レコード ヘッド データを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="0a4eb-247">ハンズ:1 に設定するには手の形のデータを記録します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="0a4eb-248">spatialMapping:空間マッピングを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="0a4eb-249">環境:環境のデータを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="0a4eb-250">名:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-250">name : Name of the recording.</span></span>
* <span data-ttu-id="0a4eb-251">singleSpatialMappingFrame:空間マッピングは 1 つのフレームのみを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="0a4eb-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="0a4eb-253">状態の記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-253">Get recording state.</span></span>

<span data-ttu-id="0a4eb-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="0a4eb-255">現在の記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-255">Stop the current recording.</span></span> <span data-ttu-id="0a4eb-256">記録は、ファイルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="0a4eb-257">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-257">Mixed Reality Capture</span></span>

<span data-ttu-id="0a4eb-258">**/api/holographic/mrc/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="0a4eb-259">デバイスから録画複合現実を削除します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="0a4eb-260">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-260">Parameters</span></span>
* <span data-ttu-id="0a4eb-261">ファイル名:削除するファイルのエンコード、名前、hex64</span><span class="sxs-lookup"><span data-stu-id="0a4eb-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="0a4eb-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="0a4eb-263">取得、既定値に、複合現実設定のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="0a4eb-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="0a4eb-265">デバイスから複合現実ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="0a4eb-266">使用 op ストリーミング ストリームのクエリ パラメーターを = です。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="0a4eb-267">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-267">Parameters</span></span>
* <span data-ttu-id="0a4eb-268">ファイル名:取得するビデオ ファイルのエンコード、名前、hex64</span><span class="sxs-lookup"><span data-stu-id="0a4eb-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="0a4eb-269">op: ストリーム</span><span class="sxs-lookup"><span data-stu-id="0a4eb-269">op : stream</span></span>

<span data-ttu-id="0a4eb-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="0a4eb-271">指定したファイルのサムネイル画像を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="0a4eb-272">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-272">Parameters</span></span>
* <span data-ttu-id="0a4eb-273">ファイル名:エンコードされる場合は、サムネイルを要求する対象のファイルの名前、hex64</span><span class="sxs-lookup"><span data-stu-id="0a4eb-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="0a4eb-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="0a4eb-275">記録された複合現実 (実行、停止) の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="0a4eb-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="0a4eb-277">デバイスに保存された複合現実ファイルの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="0a4eb-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="0a4eb-279">セットの既定値に、複合現実設定のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="0a4eb-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="0a4eb-281">複合現実の録音を開始します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="0a4eb-282">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-282">Parameters</span></span>
* <span data-ttu-id="0a4eb-283">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-284">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="0a4eb-285">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="0a4eb-286">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="0a4eb-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="0a4eb-288">停止現在混合現実の記録</span><span class="sxs-lookup"><span data-stu-id="0a4eb-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="0a4eb-289">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="0a4eb-290">複合現実の写真を撮影し、デバイス上のファイルを作成します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="0a4eb-291">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-291">Parameters</span></span>
* <span data-ttu-id="0a4eb-292">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-293">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="0a4eb-294">複合現実のストリーミング</span><span class="sxs-lookup"><span data-stu-id="0a4eb-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="0a4eb-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="0a4eb-296">フラグメント化 mp4 のチャンク ダウンロードを開始する</span><span class="sxs-lookup"><span data-stu-id="0a4eb-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="0a4eb-297">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-297">Parameters</span></span>
* <span data-ttu-id="0a4eb-298">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-299">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="0a4eb-300">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="0a4eb-301">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="0a4eb-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="0a4eb-303">フラグメント化 mp4 のチャンク ダウンロードを開始する</span><span class="sxs-lookup"><span data-stu-id="0a4eb-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="0a4eb-304">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-304">Parameters</span></span>
* <span data-ttu-id="0a4eb-305">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-306">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="0a4eb-307">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="0a4eb-308">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="0a4eb-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="0a4eb-310">フラグメント化 mp4 のチャンク ダウンロードを開始する</span><span class="sxs-lookup"><span data-stu-id="0a4eb-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="0a4eb-311">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-311">Parameters</span></span>
* <span data-ttu-id="0a4eb-312">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-313">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="0a4eb-314">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="0a4eb-315">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="0a4eb-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="0a4eb-317">フラグメント化 mp4 のチャンク ダウンロードを開始する</span><span class="sxs-lookup"><span data-stu-id="0a4eb-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="0a4eb-318">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-318">Parameters</span></span>
* <span data-ttu-id="0a4eb-319">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="0a4eb-320">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="0a4eb-321">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="0a4eb-322">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="0a4eb-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="0a4eb-323">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="0a4eb-323">Networking</span></span>

<span data-ttu-id="0a4eb-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="0a4eb-325">現在の ip 構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="0a4eb-326">OS 情報</span><span class="sxs-lookup"><span data-stu-id="0a4eb-326">OS Information</span></span>

<span data-ttu-id="0a4eb-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="0a4eb-328">オペレーティング システムの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-328">Gets operating system information</span></span>

<span data-ttu-id="0a4eb-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="0a4eb-330">コンピューター名を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-330">Gets the machine name</span></span>

<span data-ttu-id="0a4eb-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="0a4eb-332">コンピューター名を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-332">Sets the machine name</span></span>

<span data-ttu-id="0a4eb-333">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-333">Parameters</span></span>
* <span data-ttu-id="0a4eb-334">名:新しいコンピューター名、hex64 エンコードされる場合に設定するには</span><span class="sxs-lookup"><span data-stu-id="0a4eb-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="0a4eb-335">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-335">Performance data</span></span>

<span data-ttu-id="0a4eb-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="0a4eb-337">詳細でプロセスを実行の一覧を返します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="0a4eb-338">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-338">Return data</span></span>
* <span data-ttu-id="0a4eb-339">プロセスと各プロセスの詳細の一覧が JSON</span><span class="sxs-lookup"><span data-stu-id="0a4eb-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="0a4eb-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="0a4eb-341">(読み取り/書き込みの I/O、メモリの統計情報などシステム パフォーマンスの統計情報を返しますです。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="0a4eb-342">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-342">Return data</span></span>
* <span data-ttu-id="0a4eb-343">システム情報を使用して、JSON:CPU、GPU、メモリ、ネットワーク、IO</span><span class="sxs-lookup"><span data-stu-id="0a4eb-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="0a4eb-344">Power</span><span class="sxs-lookup"><span data-stu-id="0a4eb-344">Power</span></span>

<span data-ttu-id="0a4eb-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="0a4eb-346">現在のバッテリの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-346">Gets the current battery state</span></span>

<span data-ttu-id="0a4eb-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="0a4eb-348">システムの低電力状態を確認します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="0a4eb-349">リモート コントロール</span><span class="sxs-lookup"><span data-stu-id="0a4eb-349">Remote Control</span></span>

<span data-ttu-id="0a4eb-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="0a4eb-351">ターゲット デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-351">Restarts the target device</span></span>

<span data-ttu-id="0a4eb-352">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="0a4eb-353">ターゲット デバイスをシャット ダウン</span><span class="sxs-lookup"><span data-stu-id="0a4eb-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="0a4eb-354">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="0a4eb-354">Task Manager</span></span>

<span data-ttu-id="0a4eb-355">**/api/taskmanager/app (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="0a4eb-356">最新のアプリを停止します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-356">Stops a modern app</span></span>

<span data-ttu-id="0a4eb-357">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-357">Parameters</span></span>
* <span data-ttu-id="0a4eb-358">パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前</span><span class="sxs-lookup"><span data-stu-id="0a4eb-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="0a4eb-359">強制:強制的にすべてのプロセスを停止する (= [はい])</span><span class="sxs-lookup"><span data-stu-id="0a4eb-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="0a4eb-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="0a4eb-361">最新のアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-361">Starts a modern app</span></span>

<span data-ttu-id="0a4eb-362">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-362">Parameters</span></span>
* <span data-ttu-id="0a4eb-363">appid:開始するアプリの PRAID、hex64 エンコード</span><span class="sxs-lookup"><span data-stu-id="0a4eb-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="0a4eb-364">パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前</span><span class="sxs-lookup"><span data-stu-id="0a4eb-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="0a4eb-365">WiFi の管理</span><span class="sxs-lookup"><span data-stu-id="0a4eb-365">WiFi Management</span></span>

<span data-ttu-id="0a4eb-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="0a4eb-367">ワイヤレス ネットワーク インターフェイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="0a4eb-368">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-368">Return data</span></span>
* <span data-ttu-id="0a4eb-369">(GUID、説明など) の詳細を含むワイヤレス インターフェイスの一覧</span><span class="sxs-lookup"><span data-stu-id="0a4eb-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="0a4eb-370">**/api/wifi/network (削除)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="0a4eb-371">指定されたインターフェイス上のネットワークに関連付けられているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="0a4eb-372">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-372">Parameters</span></span>
* <span data-ttu-id="0a4eb-373">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="0a4eb-373">interface : network interface guid</span></span>
* <span data-ttu-id="0a4eb-374">プロファイル: プロファイル名</span><span class="sxs-lookup"><span data-stu-id="0a4eb-374">profile : profile name</span></span>

<span data-ttu-id="0a4eb-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="0a4eb-376">指定したネットワーク インターフェイス上でワイヤレス ネットワークを列挙します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="0a4eb-377">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-377">Parameters</span></span>
* <span data-ttu-id="0a4eb-378">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="0a4eb-378">interface : network interface guid</span></span>

<span data-ttu-id="0a4eb-379">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-379">Return data</span></span>
* <span data-ttu-id="0a4eb-380">ネットワーク インターフェイスの詳細に検出されたワイヤレス ネットワークの一覧</span><span class="sxs-lookup"><span data-stu-id="0a4eb-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="0a4eb-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="0a4eb-382">接続または指定されたインターフェイス上のネットワークに接続を切断</span><span class="sxs-lookup"><span data-stu-id="0a4eb-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="0a4eb-383">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-383">Parameters</span></span>
* <span data-ttu-id="0a4eb-384">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="0a4eb-384">interface : network interface guid</span></span>
* <span data-ttu-id="0a4eb-385">ssid: ssid、hex64 への接続にエンコードします。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="0a4eb-386">op: 接続または切断</span><span class="sxs-lookup"><span data-stu-id="0a4eb-386">op : connect or disconnect</span></span>
* <span data-ttu-id="0a4eb-387">createprofile: はいまたは no</span><span class="sxs-lookup"><span data-stu-id="0a4eb-387">createprofile : yes or no</span></span>
* <span data-ttu-id="0a4eb-388">キー: エンコードされた共有のキー、hex64</span><span class="sxs-lookup"><span data-stu-id="0a4eb-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="0a4eb-389">Windows パフォーマンス レコーダー</span><span class="sxs-lookup"><span data-stu-id="0a4eb-389">Windows Performance Recorder</span></span>

<span data-ttu-id="0a4eb-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="0a4eb-391">WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="0a4eb-392">ペイロード</span><span class="sxs-lookup"><span data-stu-id="0a4eb-392">Payload</span></span>
* <span data-ttu-id="0a4eb-393">準拠したマルチパートの http 本文</span><span class="sxs-lookup"><span data-stu-id="0a4eb-393">multi-part conforming http body</span></span>

<span data-ttu-id="0a4eb-394">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-394">Return data</span></span>
* <span data-ttu-id="0a4eb-395">WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-395">Returns the WPR session status.</span></span>

<span data-ttu-id="0a4eb-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="0a4eb-397">WPR セッションの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="0a4eb-398">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-398">Return data</span></span>
* <span data-ttu-id="0a4eb-399">WPR セッションの状態。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-399">WPR session status.</span></span>

<span data-ttu-id="0a4eb-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="0a4eb-401">WPR (パフォーマンス) のトレース セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="0a4eb-402">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-402">Return data</span></span>
* <span data-ttu-id="0a4eb-403">トレース ETL ファイルを返します</span><span class="sxs-lookup"><span data-stu-id="0a4eb-403">Returns the trace ETL file</span></span>

<span data-ttu-id="0a4eb-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="0a4eb-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="0a4eb-405">セッションのトレース WPR (パフォーマンス) を開始します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="0a4eb-406">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a4eb-406">Parameters</span></span>
* <span data-ttu-id="0a4eb-407">プロファイル:プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-407">profile : Profile name.</span></span> <span data-ttu-id="0a4eb-408">使用可能なプロファイル perfprofiles/profiles.json に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="0a4eb-409">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="0a4eb-409">Return data</span></span>
* <span data-ttu-id="0a4eb-410">起動時に、WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="0a4eb-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a4eb-411">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a4eb-411">See also</span></span>
* [<span data-ttu-id="0a4eb-412">Windows Device Portal のを使用</span><span class="sxs-lookup"><span data-stu-id="0a4eb-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="0a4eb-413">デバイス ポータル core API リファレンス (UWP)</span><span class="sxs-lookup"><span data-stu-id="0a4eb-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
