---
title: デバイス ポータル API リファレンス
description: HoloLens で Windows Device Portal の API リファレンス
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows Device Portal の API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694430"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="93bba-104">デバイス ポータル API リファレンス</span><span class="sxs-lookup"><span data-stu-id="93bba-104">Device portal API reference</span></span>

<span data-ttu-id="93bba-105">内のすべて、 [Windows Device Portal](using-the-windows-device-portal.md)データにアクセスし、デバイスの管理をプログラム的に使用できる REST API の上に構築されます。</span><span class="sxs-lookup"><span data-stu-id="93bba-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="93bba-106">アプリの展開</span><span class="sxs-lookup"><span data-stu-id="93bba-106">App deloyment</span></span>

<span data-ttu-id="93bba-107">**/api/app/packagemanager/package (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="93bba-108">アプリをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="93bba-108">Uninstalls an app</span></span>

<span data-ttu-id="93bba-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-109">Parameters</span></span>
* <span data-ttu-id="93bba-110">パッケージ:アンインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="93bba-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="93bba-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="93bba-112">アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="93bba-112">Installs an App</span></span>

<span data-ttu-id="93bba-113">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-113">Parameters</span></span>
* <span data-ttu-id="93bba-114">パッケージ:パッケージをインストールするのファイル名。</span><span class="sxs-lookup"><span data-stu-id="93bba-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="93bba-115">ペイロード</span><span class="sxs-lookup"><span data-stu-id="93bba-115">Payload</span></span>
* <span data-ttu-id="93bba-116">準拠したマルチパートの http 本文</span><span class="sxs-lookup"><span data-stu-id="93bba-116">multi-part conforming http body</span></span>

<span data-ttu-id="93bba-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="93bba-118">詳細と、システムにインストールされているアプリの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="93bba-119">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-119">Return data</span></span>
* <span data-ttu-id="93bba-120">詳細とインストールされているパッケージの一覧</span><span class="sxs-lookup"><span data-stu-id="93bba-120">List of installed packages with details</span></span>

<span data-ttu-id="93bba-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="93bba-122">アプリのインストールの進行状況での状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="93bba-123">ダンプの収集</span><span class="sxs-lookup"><span data-stu-id="93bba-123">Dump collection</span></span>

<span data-ttu-id="93bba-124">**/api/debug/dump/usermode/crashcontrol (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="93bba-125">サイドロードされたアプリのダンプの収集がクラッシュする無効にします。</span><span class="sxs-lookup"><span data-stu-id="93bba-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="93bba-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-126">Parameters</span></span>
* <span data-ttu-id="93bba-127">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="93bba-127">packageFullname : package name</span></span>

<span data-ttu-id="93bba-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="93bba-129">クラッシュ ダンプの収集にサイドロードしたアプリの設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="93bba-130">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-130">Parameters</span></span>
* <span data-ttu-id="93bba-131">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="93bba-131">packageFullname : package name</span></span>

<span data-ttu-id="93bba-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="93bba-133">有効にし、サイドロードされたアプリのダンプ制御の設定の設定</span><span class="sxs-lookup"><span data-stu-id="93bba-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="93bba-134">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-134">Parameters</span></span>
* <span data-ttu-id="93bba-135">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="93bba-135">packageFullname : package name</span></span>

<span data-ttu-id="93bba-136">**/api/debug/dump/usermode/crashdump (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="93bba-137">サイドロードされたアプリのクラッシュ ダンプを削除します。</span><span class="sxs-lookup"><span data-stu-id="93bba-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="93bba-138">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-138">Parameters</span></span>
* <span data-ttu-id="93bba-139">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="93bba-139">packageFullname : package name</span></span>
* <span data-ttu-id="93bba-140">ファイル名: ダンプ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="93bba-140">fileName : dump file name</span></span>

<span data-ttu-id="93bba-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="93bba-142">サイドロードされたアプリのクラッシュ ダンプを取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="93bba-143">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-143">Parameters</span></span>
* <span data-ttu-id="93bba-144">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="93bba-144">packageFullname : package name</span></span>
* <span data-ttu-id="93bba-145">ファイル名: ダンプ ファイルの名前</span><span class="sxs-lookup"><span data-stu-id="93bba-145">fileName : dump file name</span></span>

<span data-ttu-id="93bba-146">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-146">Return data</span></span>
* <span data-ttu-id="93bba-147">ダンプ ファイル。</span><span class="sxs-lookup"><span data-stu-id="93bba-147">Dump file.</span></span> <span data-ttu-id="93bba-148">WinDbg または Visual Studio での検査します。</span><span class="sxs-lookup"><span data-stu-id="93bba-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="93bba-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="93bba-150">サイドロードしたアプリのすべてのクラッシュ ダンプのリストを返します</span><span class="sxs-lookup"><span data-stu-id="93bba-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="93bba-151">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-151">Return data</span></span>
* <span data-ttu-id="93bba-152">サイド ロード アプリごとの一連のクラッシュ ダンプします。</span><span class="sxs-lookup"><span data-stu-id="93bba-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="93bba-153">ETW</span><span class="sxs-lookup"><span data-stu-id="93bba-153">ETW</span></span>

<span data-ttu-id="93bba-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="93bba-155">登録されているプロバイダーを列挙します。</span><span class="sxs-lookup"><span data-stu-id="93bba-155">Enumerates registered providers</span></span>

<span data-ttu-id="93bba-156">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-156">Return data</span></span>
* <span data-ttu-id="93bba-157">プロバイダー、フレンドリ名と GUID の一覧</span><span class="sxs-lookup"><span data-stu-id="93bba-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="93bba-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="93bba-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="93bba-159">リアルタイムの ETW セッションを作成します。websocket 経由で管理します。</span><span class="sxs-lookup"><span data-stu-id="93bba-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="93bba-160">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-160">Return data</span></span>
* <span data-ttu-id="93bba-161">有効なプロバイダーから ETW イベント</span><span class="sxs-lookup"><span data-stu-id="93bba-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="93bba-162">ホログラフィック OS</span><span class="sxs-lookup"><span data-stu-id="93bba-162">Holographic OS</span></span>

<span data-ttu-id="93bba-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="93bba-164">システムに登録されていない HoloLens 特定 ETW プロバイダーの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="93bba-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="93bba-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="93bba-166">実行されているすべてのサービスの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="93bba-166">Returns the states of all services running.</span></span>

<span data-ttu-id="93bba-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="93bba-168">ミリメートル単位ストアド IPD (Interpupillary 距離) を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="93bba-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="93bba-170">IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-170">Sets the IPD</span></span>

<span data-ttu-id="93bba-171">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-171">Parameters</span></span>
* <span data-ttu-id="93bba-172">ipd:ミリメートル単位で設定される新しい IPD 値</span><span class="sxs-lookup"><span data-stu-id="93bba-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="93bba-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="93bba-174">Device Portal の HTTPS 要件を取得する</span><span class="sxs-lookup"><span data-stu-id="93bba-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="93bba-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="93bba-176">デバイスのポータルの HTTPS 要件を設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="93bba-177">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-177">Parameters</span></span>
* <span data-ttu-id="93bba-178">必須: yes、no または既定値</span><span class="sxs-lookup"><span data-stu-id="93bba-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="93bba-179">Holographic Perception</span><span class="sxs-lookup"><span data-stu-id="93bba-179">Holographic Perception</span></span>

<span data-ttu-id="93bba-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="93bba-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="93bba-181">Websocket のアップグレードを受け取り、30 fps で更新プログラムを送信する perception クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="93bba-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="93bba-182">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-182">Parameters</span></span>
* <span data-ttu-id="93bba-183">clientmode:"active"強制的 visual 追跡モード受動的に確立されることはできません</span><span class="sxs-lookup"><span data-stu-id="93bba-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="93bba-184">Holographic 温度</span><span class="sxs-lookup"><span data-stu-id="93bba-184">Holographic Thermal</span></span>

<span data-ttu-id="93bba-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="93bba-186">(通常 0、1 ウォーム、重要な 2) のデバイスの温度のステージを取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="93bba-187">Perception シミュレーション コントロール</span><span class="sxs-lookup"><span data-stu-id="93bba-187">Perception Simulation Control</span></span>

<span data-ttu-id="93bba-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="93bba-189">シミュレーションのモードを取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-189">Get the simulation mode</span></span>

<span data-ttu-id="93bba-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="93bba-191">シミュレーションのモードを設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-191">Set the simulation mode</span></span>

<span data-ttu-id="93bba-192">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-192">Parameters</span></span>
* <span data-ttu-id="93bba-193">モード: シミュレーション モード: 既定では、シミュレーション、リモートのレガシ</span><span class="sxs-lookup"><span data-stu-id="93bba-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="93bba-194">**/api/holographic/simulation/control/stream (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="93bba-195">コントロールのストリームを削除します。</span><span class="sxs-lookup"><span data-stu-id="93bba-195">Delete a control stream.</span></span>

<span data-ttu-id="93bba-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="93bba-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="93bba-197">コントロールのストリームの web ソケット接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="93bba-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="93bba-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="93bba-199">コントロールのストリームを作成する (優先度が必要) または作成されたストリーム (必要な streamId) にデータをポストします。</span><span class="sxs-lookup"><span data-stu-id="93bba-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="93bba-200">ポストされたデータは、' アプリケーションまたはオクテット ストリーム ' 型のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="93bba-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="93bba-201">Perception シミュレーションの再生</span><span class="sxs-lookup"><span data-stu-id="93bba-201">Perception Simulation Playback</span></span>

<span data-ttu-id="93bba-202">**/api/holographic/simulation/playback/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="93bba-203">録画を削除します。</span><span class="sxs-lookup"><span data-stu-id="93bba-203">Delete a recording.</span></span>

<span data-ttu-id="93bba-204">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-204">Parameters</span></span>
* <span data-ttu-id="93bba-205">録音:削除する記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="93bba-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="93bba-207">録画をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="93bba-207">Upload a recording.</span></span>

<span data-ttu-id="93bba-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="93bba-209">すべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-209">Get all recordings.</span></span>

<span data-ttu-id="93bba-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="93bba-211">録画の現在の再生状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="93bba-212">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-212">Parameters</span></span>
* <span data-ttu-id="93bba-213">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-213">recording : Name of recording.</span></span>

<span data-ttu-id="93bba-214">**/api/holographic/simulation/playback/session/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="93bba-215">録画をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="93bba-215">Unload a recording.</span></span>

<span data-ttu-id="93bba-216">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-216">Parameters</span></span>
* <span data-ttu-id="93bba-217">録音:アンロードする記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="93bba-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="93bba-219">録画を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="93bba-219">Load a recording.</span></span>

<span data-ttu-id="93bba-220">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-220">Parameters</span></span>
* <span data-ttu-id="93bba-221">録音:記録を読み込むの名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="93bba-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="93bba-223">読み込まれたすべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-223">Get all loaded recordings.</span></span>

<span data-ttu-id="93bba-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="93bba-225">記録を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="93bba-225">Pause a recording.</span></span>

<span data-ttu-id="93bba-226">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-226">Parameters</span></span>
* <span data-ttu-id="93bba-227">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-227">recording : Name of recording.</span></span>

<span data-ttu-id="93bba-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="93bba-229">記録を再生します。</span><span class="sxs-lookup"><span data-stu-id="93bba-229">Play a recording.</span></span>

<span data-ttu-id="93bba-230">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-230">Parameters</span></span>
* <span data-ttu-id="93bba-231">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-231">recording : Name of recording.</span></span>

<span data-ttu-id="93bba-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="93bba-233">録画を停止します。</span><span class="sxs-lookup"><span data-stu-id="93bba-233">Stop a recording.</span></span>

<span data-ttu-id="93bba-234">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-234">Parameters</span></span>
* <span data-ttu-id="93bba-235">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-235">recording : Name of recording.</span></span>

<span data-ttu-id="93bba-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="93bba-237">読み込まれた記録では、データの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="93bba-238">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-238">Parameters</span></span>
* <span data-ttu-id="93bba-239">録音:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="93bba-240">Perception シミュレーションの記録</span><span class="sxs-lookup"><span data-stu-id="93bba-240">Perception Simulation Recording</span></span>

<span data-ttu-id="93bba-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="93bba-242">録画を開始します。</span><span class="sxs-lookup"><span data-stu-id="93bba-242">Start a recording.</span></span> <span data-ttu-id="93bba-243">1 つの記録のみを一度にアクティブにできます。</span><span class="sxs-lookup"><span data-stu-id="93bba-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="93bba-244">Head、手、spatialMapping または環境のいずれかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93bba-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="93bba-245">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-245">Parameters</span></span>
* <span data-ttu-id="93bba-246">ヘッド:レコード ヘッド データを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="93bba-247">ハンズ:1 に設定するには手の形のデータを記録します。</span><span class="sxs-lookup"><span data-stu-id="93bba-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="93bba-248">spatialMapping:空間マッピングを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="93bba-249">環境:環境のデータを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="93bba-250">名:記録の名前です。</span><span class="sxs-lookup"><span data-stu-id="93bba-250">name : Name of the recording.</span></span>
* <span data-ttu-id="93bba-251">singleSpatialMappingFrame:空間マッピングは 1 つのフレームのみを記録する、1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="93bba-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="93bba-253">状態の記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-253">Get recording state.</span></span>

<span data-ttu-id="93bba-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="93bba-255">現在の記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="93bba-255">Stop the current recording.</span></span> <span data-ttu-id="93bba-256">記録は、ファイルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="93bba-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="93bba-257">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="93bba-257">Mixed Reality Capture</span></span>

<span data-ttu-id="93bba-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="93bba-259">デバイスから複合現実ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="93bba-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="93bba-260">使用 op ストリーミング ストリームのクエリ パラメーターを = です。</span><span class="sxs-lookup"><span data-stu-id="93bba-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="93bba-261">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-261">Parameters</span></span>
* <span data-ttu-id="93bba-262">ファイル名:取得するビデオ ファイルのエンコード、名前、hex64</span><span class="sxs-lookup"><span data-stu-id="93bba-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="93bba-263">op: ストリーム</span><span class="sxs-lookup"><span data-stu-id="93bba-263">op : stream</span></span>

<span data-ttu-id="93bba-264">**/api/holographic/mrc/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="93bba-265">デバイスから録画複合現実を削除します。</span><span class="sxs-lookup"><span data-stu-id="93bba-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="93bba-266">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-266">Parameters</span></span>
* <span data-ttu-id="93bba-267">ファイル名:削除するファイルのエンコード、名前、hex64</span><span class="sxs-lookup"><span data-stu-id="93bba-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="93bba-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="93bba-269">デバイスに保存された複合現実ファイルの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="93bba-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="93bba-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="93bba-271">複合現実の写真を撮影し、デバイス上のファイルを作成します</span><span class="sxs-lookup"><span data-stu-id="93bba-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="93bba-272">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-272">Parameters</span></span>
* <span data-ttu-id="93bba-273">holo: キャプチャ ホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-274">pv: キャプチャ PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-275">RenderFromCamera:写真/ビデオのカメラの観点からレンダリングを (HoloLens 2 のみ): true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="93bba-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="93bba-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="93bba-277">取得、既定値に、複合現実設定のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="93bba-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="93bba-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="93bba-279">セットの既定値に、複合現実設定のキャプチャ。</span><span class="sxs-lookup"><span data-stu-id="93bba-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="93bba-280">これらの設定の一部は、システムの MRC 写真とビデオのキャプチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="93bba-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="93bba-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="93bba-282">記録された複合現実 (実行、停止) の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="93bba-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="93bba-284">指定したファイルのサムネイル画像を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="93bba-285">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-285">Parameters</span></span>
* <span data-ttu-id="93bba-286">ファイル名:エンコードされる場合は、サムネイルを要求する対象のファイルの名前、hex64</span><span class="sxs-lookup"><span data-stu-id="93bba-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="93bba-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="93bba-288">複合現実の録音を開始します。</span><span class="sxs-lookup"><span data-stu-id="93bba-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="93bba-289">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-289">Parameters</span></span>
* <span data-ttu-id="93bba-290">holo: キャプチャ ホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-291">pv: キャプチャ PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-292">mic: キャプチャ マイク: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-293">ループバック: アプリの音声のキャプチャ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-294">RenderFromCamera:写真/ビデオのカメラの観点からレンダリングを (HoloLens 2 のみ): true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="93bba-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="93bba-295">vstab:有効にするビデオ安定化の (HoloLens 2 のみ): true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="93bba-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="93bba-296">vstabbuffer:ビデオ安定化バッファーの待機時間を (HoloLens 2 のみ):0 ~ 30 フレーム (既定値は 15 フレーム)</span><span class="sxs-lookup"><span data-stu-id="93bba-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="93bba-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="93bba-298">停止現在混合現実の記録</span><span class="sxs-lookup"><span data-stu-id="93bba-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="93bba-299">複合現実のストリーミング</span><span class="sxs-lookup"><span data-stu-id="93bba-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="93bba-300">HoloLens では、フラグメント化 mp4 のチャンクのダウンロードを使用して複合現実のライブ プレビューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="93bba-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="93bba-301">複合現実のストリームは、キャプチャされるものを制御するパラメーターの同じセットを共有します。</span><span class="sxs-lookup"><span data-stu-id="93bba-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="93bba-302">holo: キャプチャ ホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="93bba-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="93bba-303">pv: キャプチャ PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="93bba-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="93bba-304">mic: キャプチャ マイク: true または false</span><span class="sxs-lookup"><span data-stu-id="93bba-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="93bba-305">ループバック: アプリの音声のキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="93bba-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="93bba-306">指定しないと、これらの場合: ホログラム、カメラの写真とビデオ、およびアプリの音声がキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="93bba-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="93bba-307">指定されている場合: 指定されていないパラメーターは既定で false</span><span class="sxs-lookup"><span data-stu-id="93bba-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="93bba-308">省略可能なパラメーター (HoloLens 2 のみ)</span><span class="sxs-lookup"><span data-stu-id="93bba-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="93bba-309">RenderFromCamera: 写真/ビデオのカメラの観点からを表示: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="93bba-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="93bba-310">vstab: ビデオ安定化を有効にする: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="93bba-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="93bba-311">vstabbuffer: ビデオ安定化バッファーの待機時間。0 ~ 30 フレーム (既定値は 15 フレーム)</span><span class="sxs-lookup"><span data-stu-id="93bba-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="93bba-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="93bba-313">1280x720p 30 fps 5Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="93bba-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="93bba-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="93bba-315">1280x720p 30 fps 5Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="93bba-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="93bba-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="93bba-317">854x480p 30 fps 2.5Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="93bba-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="93bba-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="93bba-319">428x240p 15 fps 0.6Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="93bba-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="93bba-320">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="93bba-320">Networking</span></span>

<span data-ttu-id="93bba-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="93bba-322">現在の ip 構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="93bba-323">OS 情報</span><span class="sxs-lookup"><span data-stu-id="93bba-323">OS Information</span></span>

<span data-ttu-id="93bba-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="93bba-325">オペレーティング システムの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-325">Gets operating system information</span></span>

<span data-ttu-id="93bba-326">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="93bba-327">コンピューター名を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-327">Gets the machine name</span></span>

<span data-ttu-id="93bba-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="93bba-329">コンピューター名を設定します。</span><span class="sxs-lookup"><span data-stu-id="93bba-329">Sets the machine name</span></span>

<span data-ttu-id="93bba-330">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-330">Parameters</span></span>
* <span data-ttu-id="93bba-331">名:新しいコンピューター名、hex64 エンコードされる場合に設定するには</span><span class="sxs-lookup"><span data-stu-id="93bba-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="93bba-332">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="93bba-332">Performance data</span></span>

<span data-ttu-id="93bba-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="93bba-334">詳細でプロセスを実行の一覧を返します</span><span class="sxs-lookup"><span data-stu-id="93bba-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="93bba-335">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-335">Return data</span></span>
* <span data-ttu-id="93bba-336">プロセスと各プロセスの詳細の一覧が JSON</span><span class="sxs-lookup"><span data-stu-id="93bba-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="93bba-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="93bba-338">(読み取り/書き込みの I/O、メモリの統計情報などシステム パフォーマンスの統計情報を返しますです。</span><span class="sxs-lookup"><span data-stu-id="93bba-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="93bba-339">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-339">Return data</span></span>
* <span data-ttu-id="93bba-340">システム情報を使用して、JSON:CPU、GPU、メモリ、ネットワーク、IO</span><span class="sxs-lookup"><span data-stu-id="93bba-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="93bba-341">Power</span><span class="sxs-lookup"><span data-stu-id="93bba-341">Power</span></span>

<span data-ttu-id="93bba-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="93bba-343">現在のバッテリの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-343">Gets the current battery state</span></span>

<span data-ttu-id="93bba-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="93bba-345">システムの低電力状態を確認します</span><span class="sxs-lookup"><span data-stu-id="93bba-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="93bba-346">リモート コントロール</span><span class="sxs-lookup"><span data-stu-id="93bba-346">Remote Control</span></span>

<span data-ttu-id="93bba-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="93bba-348">ターゲット デバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="93bba-348">Restarts the target device</span></span>

<span data-ttu-id="93bba-349">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="93bba-350">ターゲット デバイスをシャット ダウン</span><span class="sxs-lookup"><span data-stu-id="93bba-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="93bba-351">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="93bba-351">Task Manager</span></span>

<span data-ttu-id="93bba-352">**/api/taskmanager/app (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="93bba-353">最新のアプリを停止します。</span><span class="sxs-lookup"><span data-stu-id="93bba-353">Stops a modern app</span></span>

<span data-ttu-id="93bba-354">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-354">Parameters</span></span>
* <span data-ttu-id="93bba-355">パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前</span><span class="sxs-lookup"><span data-stu-id="93bba-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="93bba-356">強制:強制的にすべてのプロセスを停止する (= [はい])</span><span class="sxs-lookup"><span data-stu-id="93bba-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="93bba-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="93bba-358">最新のアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="93bba-358">Starts a modern app</span></span>

<span data-ttu-id="93bba-359">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-359">Parameters</span></span>
* <span data-ttu-id="93bba-360">appid:開始するアプリの PRAID、hex64 エンコード</span><span class="sxs-lookup"><span data-stu-id="93bba-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="93bba-361">パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前</span><span class="sxs-lookup"><span data-stu-id="93bba-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="93bba-362">WiFi の管理</span><span class="sxs-lookup"><span data-stu-id="93bba-362">WiFi Management</span></span>

<span data-ttu-id="93bba-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="93bba-364">ワイヤレス ネットワーク インターフェイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="93bba-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="93bba-365">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-365">Return data</span></span>
* <span data-ttu-id="93bba-366">(GUID、説明など) の詳細を含むワイヤレス インターフェイスの一覧</span><span class="sxs-lookup"><span data-stu-id="93bba-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="93bba-367">**/api/wifi/network (削除)**</span><span class="sxs-lookup"><span data-stu-id="93bba-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="93bba-368">指定されたインターフェイス上のネットワークに関連付けられているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="93bba-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="93bba-369">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-369">Parameters</span></span>
* <span data-ttu-id="93bba-370">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="93bba-370">interface : network interface guid</span></span>
* <span data-ttu-id="93bba-371">プロファイル: プロファイル名</span><span class="sxs-lookup"><span data-stu-id="93bba-371">profile : profile name</span></span>

<span data-ttu-id="93bba-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="93bba-373">指定したネットワーク インターフェイス上でワイヤレス ネットワークを列挙します。</span><span class="sxs-lookup"><span data-stu-id="93bba-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="93bba-374">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-374">Parameters</span></span>
* <span data-ttu-id="93bba-375">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="93bba-375">interface : network interface guid</span></span>

<span data-ttu-id="93bba-376">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-376">Return data</span></span>
* <span data-ttu-id="93bba-377">ネットワーク インターフェイスの詳細に検出されたワイヤレス ネットワークの一覧</span><span class="sxs-lookup"><span data-stu-id="93bba-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="93bba-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="93bba-379">接続または指定されたインターフェイス上のネットワークに接続を切断</span><span class="sxs-lookup"><span data-stu-id="93bba-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="93bba-380">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-380">Parameters</span></span>
* <span data-ttu-id="93bba-381">インターフェイス: ネットワーク インターフェイスの guid</span><span class="sxs-lookup"><span data-stu-id="93bba-381">interface : network interface guid</span></span>
* <span data-ttu-id="93bba-382">ssid: ssid、hex64 への接続にエンコードします。</span><span class="sxs-lookup"><span data-stu-id="93bba-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="93bba-383">op: 接続または切断</span><span class="sxs-lookup"><span data-stu-id="93bba-383">op : connect or disconnect</span></span>
* <span data-ttu-id="93bba-384">createprofile: はいまたは no</span><span class="sxs-lookup"><span data-stu-id="93bba-384">createprofile : yes or no</span></span>
* <span data-ttu-id="93bba-385">キー: エンコードされた共有のキー、hex64</span><span class="sxs-lookup"><span data-stu-id="93bba-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="93bba-386">Windows パフォーマンス レコーダー</span><span class="sxs-lookup"><span data-stu-id="93bba-386">Windows Performance Recorder</span></span>

<span data-ttu-id="93bba-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="93bba-388">WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="93bba-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="93bba-389">ペイロード</span><span class="sxs-lookup"><span data-stu-id="93bba-389">Payload</span></span>
* <span data-ttu-id="93bba-390">準拠したマルチパートの http 本文</span><span class="sxs-lookup"><span data-stu-id="93bba-390">multi-part conforming http body</span></span>

<span data-ttu-id="93bba-391">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-391">Return data</span></span>
* <span data-ttu-id="93bba-392">WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="93bba-392">Returns the WPR session status.</span></span>

<span data-ttu-id="93bba-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="93bba-394">WPR セッションの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bba-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="93bba-395">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-395">Return data</span></span>
* <span data-ttu-id="93bba-396">WPR セッションの状態。</span><span class="sxs-lookup"><span data-stu-id="93bba-396">WPR session status.</span></span>

<span data-ttu-id="93bba-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="93bba-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="93bba-398">WPR (パフォーマンス) のトレース セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="93bba-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="93bba-399">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-399">Return data</span></span>
* <span data-ttu-id="93bba-400">トレース ETL ファイルを返します</span><span class="sxs-lookup"><span data-stu-id="93bba-400">Returns the trace ETL file</span></span>

<span data-ttu-id="93bba-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="93bba-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="93bba-402">セッションのトレース WPR (パフォーマンス) を開始します。</span><span class="sxs-lookup"><span data-stu-id="93bba-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="93bba-403">Parameters</span><span class="sxs-lookup"><span data-stu-id="93bba-403">Parameters</span></span>
* <span data-ttu-id="93bba-404">プロファイル:プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="93bba-404">profile : Profile name.</span></span> <span data-ttu-id="93bba-405">使用可能なプロファイル perfprofiles/profiles.json に格納されます。</span><span class="sxs-lookup"><span data-stu-id="93bba-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="93bba-406">戻り値のデータ</span><span class="sxs-lookup"><span data-stu-id="93bba-406">Return data</span></span>
* <span data-ttu-id="93bba-407">起動時に、WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="93bba-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="93bba-408">関連項目</span><span class="sxs-lookup"><span data-stu-id="93bba-408">See also</span></span>
* [<span data-ttu-id="93bba-409">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="93bba-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="93bba-410">デバイス ポータル core API リファレンス (UWP)</span><span class="sxs-lookup"><span data-stu-id="93bba-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
