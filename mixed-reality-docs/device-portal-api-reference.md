---
title: Device Portal API リファレンス
description: HoloLens の Windows デバイスポータルの API リファレンス
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows デバイスポータル、API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451327"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="e4b72-104">Device Portal API リファレンス</span><span class="sxs-lookup"><span data-stu-id="e4b72-104">Device portal API reference</span></span>

<span data-ttu-id="e4b72-105">[Windows デバイスポータル](using-the-windows-device-portal.md)のすべての機能は REST API の上に構築されており、データにアクセスしたり、デバイスをプログラムで制御したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="e4b72-106">アプリの撮る</span><span class="sxs-lookup"><span data-stu-id="e4b72-106">App deloyment</span></span>

<span data-ttu-id="e4b72-107">**/api/app/packagemanager/package (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="e4b72-108">アプリをアンインストールします</span><span class="sxs-lookup"><span data-stu-id="e4b72-108">Uninstalls an app</span></span>

<span data-ttu-id="e4b72-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-109">Parameters</span></span>
* <span data-ttu-id="e4b72-110">パッケージ: アンインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="e4b72-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="e4b72-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="e4b72-112">アプリをインストールします</span><span class="sxs-lookup"><span data-stu-id="e4b72-112">Installs an App</span></span>

<span data-ttu-id="e4b72-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-113">Parameters</span></span>
* <span data-ttu-id="e4b72-114">パッケージ: インストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="e4b72-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="e4b72-115">ペイロード</span><span class="sxs-lookup"><span data-stu-id="e4b72-115">Payload</span></span>
* <span data-ttu-id="e4b72-116">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="e4b72-116">multi-part conforming http body</span></span>

<span data-ttu-id="e4b72-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="e4b72-118">システムにインストールされているアプリの一覧を詳細と共に取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="e4b72-119">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-119">Return data</span></span>
* <span data-ttu-id="e4b72-120">インストールされているパッケージの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="e4b72-120">List of installed packages with details</span></span>

<span data-ttu-id="e4b72-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="e4b72-122">進行中のアプリのインストールの状態を取得します</span><span class="sxs-lookup"><span data-stu-id="e4b72-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="e4b72-123">ダンプの収集</span><span class="sxs-lookup"><span data-stu-id="e4b72-123">Dump collection</span></span>

<span data-ttu-id="e4b72-124">**/api/debug/dump/usermode/crashcontrol (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="e4b72-125">サイドロードアプリのクラッシュダンプの収集を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e4b72-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="e4b72-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-126">Parameters</span></span>
* <span data-ttu-id="e4b72-127">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="e4b72-127">packageFullname : package name</span></span>

<span data-ttu-id="e4b72-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="e4b72-129">サイドロード apps のクラッシュダンプの収集の設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="e4b72-130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-130">Parameters</span></span>
* <span data-ttu-id="e4b72-131">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="e4b72-131">packageFullname : package name</span></span>

<span data-ttu-id="e4b72-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="e4b72-133">サイドロードアプリのダンプ制御設定を有効にして設定します</span><span class="sxs-lookup"><span data-stu-id="e4b72-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="e4b72-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-134">Parameters</span></span>
* <span data-ttu-id="e4b72-135">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="e4b72-135">packageFullname : package name</span></span>

<span data-ttu-id="e4b72-136">**/api/debug/dump/usermode/crashdump (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="e4b72-137">サイドロードアプリのクラッシュダンプを削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="e4b72-138">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-138">Parameters</span></span>
* <span data-ttu-id="e4b72-139">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="e4b72-139">packageFullname : package name</span></span>
* <span data-ttu-id="e4b72-140">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="e4b72-140">fileName : dump file name</span></span>

<span data-ttu-id="e4b72-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="e4b72-142">サイドロードアプリのクラッシュダンプを取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="e4b72-143">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-143">Parameters</span></span>
* <span data-ttu-id="e4b72-144">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="e4b72-144">packageFullname : package name</span></span>
* <span data-ttu-id="e4b72-145">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="e4b72-145">fileName : dump file name</span></span>

<span data-ttu-id="e4b72-146">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-146">Return data</span></span>
* <span data-ttu-id="e4b72-147">ダンプファイル。</span><span class="sxs-lookup"><span data-stu-id="e4b72-147">Dump file.</span></span> <span data-ttu-id="e4b72-148">WinDbg または Visual Studio を使用して検査する</span><span class="sxs-lookup"><span data-stu-id="e4b72-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="e4b72-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="e4b72-150">サイドロードアプリのすべてのクラッシュダンプの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="e4b72-151">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-151">Return data</span></span>
* <span data-ttu-id="e4b72-152">サイドロードされたアプリごとのクラッシュダンプの一覧</span><span class="sxs-lookup"><span data-stu-id="e4b72-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="e4b72-153">ETW</span><span class="sxs-lookup"><span data-stu-id="e4b72-153">ETW</span></span>

<span data-ttu-id="e4b72-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="e4b72-155">登録されたプロバイダーを列挙します</span><span class="sxs-lookup"><span data-stu-id="e4b72-155">Enumerates registered providers</span></span>

<span data-ttu-id="e4b72-156">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-156">Return data</span></span>
* <span data-ttu-id="e4b72-157">プロバイダー、フレンドリ名、GUID の一覧</span><span class="sxs-lookup"><span data-stu-id="e4b72-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="e4b72-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="e4b72-159">リアルタイム ETW セッションを作成します。websocket 経由で管理されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="e4b72-160">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-160">Return data</span></span>
* <span data-ttu-id="e4b72-161">有効なプロバイダーからの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="e4b72-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="e4b72-162">ホログラフィック OS</span><span class="sxs-lookup"><span data-stu-id="e4b72-162">Holographic OS</span></span>

<span data-ttu-id="e4b72-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="e4b72-164">システムに登録されていない HoloLens 固有の ETW プロバイダーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="e4b72-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="e4b72-166">実行中のすべてのサービスの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-166">Returns the states of all services running.</span></span>

<span data-ttu-id="e4b72-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="e4b72-168">格納されている IPD (Interpupillary distance) をミリメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="e4b72-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="e4b72-170">IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-170">Sets the IPD</span></span>

<span data-ttu-id="e4b72-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-171">Parameters</span></span>
* <span data-ttu-id="e4b72-172">ipd: mm で設定する新しい IPD 値</span><span class="sxs-lookup"><span data-stu-id="e4b72-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="e4b72-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="e4b72-174">Device Portal の HTTPS 要件を取得する</span><span class="sxs-lookup"><span data-stu-id="e4b72-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="e4b72-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="e4b72-176">デバイスポータルの HTTPS 要件を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="e4b72-177">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-177">Parameters</span></span>
* <span data-ttu-id="e4b72-178">必須: はい、いいえ、または既定値</span><span class="sxs-lookup"><span data-stu-id="e4b72-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="e4b72-179">Holographic の認識</span><span class="sxs-lookup"><span data-stu-id="e4b72-179">Holographic Perception</span></span>

<span data-ttu-id="e4b72-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="e4b72-181">Websocket のアップグレードを受け入れ、30 fps で更新を送信する認識クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="e4b72-182">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-182">Parameters</span></span>
* <span data-ttu-id="e4b72-183">clientmode: "active" は、受動的に確立できないときにビジュアル追跡モードを強制します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="e4b72-184">Holographic Thermal</span><span class="sxs-lookup"><span data-stu-id="e4b72-184">Holographic Thermal</span></span>

<span data-ttu-id="e4b72-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="e4b72-186">デバイスの温度ステージを取得する (通常は0、1ウォーム、2重大)</span><span class="sxs-lookup"><span data-stu-id="e4b72-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="e4b72-187">認識シミュレーションの制御</span><span class="sxs-lookup"><span data-stu-id="e4b72-187">Perception Simulation Control</span></span>

<span data-ttu-id="e4b72-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="e4b72-189">シミュレーションモードを取得する</span><span class="sxs-lookup"><span data-stu-id="e4b72-189">Get the simulation mode</span></span>

<span data-ttu-id="e4b72-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="e4b72-191">シミュレーションモードの設定</span><span class="sxs-lookup"><span data-stu-id="e4b72-191">Set the simulation mode</span></span>

<span data-ttu-id="e4b72-192">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-192">Parameters</span></span>
* <span data-ttu-id="e4b72-193">モード: シミュレーションモード: 既定、シミュレーション、リモート、レガシ</span><span class="sxs-lookup"><span data-stu-id="e4b72-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="e4b72-194">**/api/holographic/simulation/control/stream (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="e4b72-195">コントロールストリームを削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-195">Delete a control stream.</span></span>

<span data-ttu-id="e4b72-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="e4b72-197">コントロールストリームの web ソケット接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="e4b72-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="e4b72-199">コントロールストリームを作成するか (優先順位が必要)、作成されたストリームにデータを post します (streamId が必要)。</span><span class="sxs-lookup"><span data-stu-id="e4b72-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="e4b72-200">ポストされたデータは ' application/オクテット-stream ' 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b72-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="e4b72-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="e4b72-202">"シミュレーション" モードで、システムに表示されるコンテンツを含むシミュレーションビデオストリームを要求します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="e4b72-203">単純なフォーマット記述子ヘッダーが最初に送信され、その後に h.264 でエンコードされたテクスチャが続きます。それぞれのヘッダーには、目のインデックスとテクスチャサイズが示されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="e4b72-204">認識シミュレーションの再生</span><span class="sxs-lookup"><span data-stu-id="e4b72-204">Perception Simulation Playback</span></span>

<span data-ttu-id="e4b72-205">**/api/holographic/simulation/playback/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="e4b72-206">記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-206">Delete a recording.</span></span>

<span data-ttu-id="e4b72-207">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-207">Parameters</span></span>
* <span data-ttu-id="e4b72-208">記録: 削除する記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="e4b72-209">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="e4b72-210">記録をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="e4b72-210">Upload a recording.</span></span>

<span data-ttu-id="e4b72-211">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="e4b72-212">すべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-212">Get all recordings.</span></span>

<span data-ttu-id="e4b72-213">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="e4b72-214">記録の現在の再生状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="e4b72-215">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-215">Parameters</span></span>
* <span data-ttu-id="e4b72-216">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-216">recording : Name of recording.</span></span>

<span data-ttu-id="e4b72-217">**/api/holographic/simulation/playback/session/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="e4b72-218">記録をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="e4b72-218">Unload a recording.</span></span>

<span data-ttu-id="e4b72-219">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-219">Parameters</span></span>
* <span data-ttu-id="e4b72-220">記録: アンロードする記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="e4b72-221">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="e4b72-222">記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-222">Load a recording.</span></span>

<span data-ttu-id="e4b72-223">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-223">Parameters</span></span>
* <span data-ttu-id="e4b72-224">記録: 読み込む記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="e4b72-225">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="e4b72-226">読み込まれたすべての録音を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-226">Get all loaded recordings.</span></span>

<span data-ttu-id="e4b72-227">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="e4b72-228">記録を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-228">Pause a recording.</span></span>

<span data-ttu-id="e4b72-229">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-229">Parameters</span></span>
* <span data-ttu-id="e4b72-230">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-230">recording : Name of recording.</span></span>

<span data-ttu-id="e4b72-231">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="e4b72-232">録音を再生します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-232">Play a recording.</span></span>

<span data-ttu-id="e4b72-233">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-233">Parameters</span></span>
* <span data-ttu-id="e4b72-234">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-234">recording : Name of recording.</span></span>

<span data-ttu-id="e4b72-235">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="e4b72-236">記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-236">Stop a recording.</span></span>

<span data-ttu-id="e4b72-237">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-237">Parameters</span></span>
* <span data-ttu-id="e4b72-238">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-238">recording : Name of recording.</span></span>

<span data-ttu-id="e4b72-239">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="e4b72-240">読み込まれた記録のデータの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="e4b72-241">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-241">Parameters</span></span>
* <span data-ttu-id="e4b72-242">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="e4b72-243">認識のシミュレーション記録</span><span class="sxs-lookup"><span data-stu-id="e4b72-243">Perception Simulation Recording</span></span>

<span data-ttu-id="e4b72-244">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="e4b72-245">記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-245">Start a recording.</span></span> <span data-ttu-id="e4b72-246">一度にアクティブにできる記録は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="e4b72-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="e4b72-247">ヘッド、ハンド、spatialMapping、または環境のいずれかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b72-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="e4b72-248">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-248">Parameters</span></span>
* <span data-ttu-id="e4b72-249">head: 1 に設定すると、ヘッドデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="e4b72-250">手: 1 に設定すると、手のデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="e4b72-251">spatialMapping: 空間マッピングを記録するには、1に設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="e4b72-252">環境: 1 に設定すると、環境データが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="e4b72-253">名前: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="e4b72-253">name : Name of the recording.</span></span>
* <span data-ttu-id="e4b72-254">singleSpatialMappingFrame: 1 に設定すると、空間マッピングフレームが1つだけ記録されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="e4b72-255">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="e4b72-256">記録の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-256">Get recording state.</span></span>

<span data-ttu-id="e4b72-257">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="e4b72-258">現在の記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-258">Stop the current recording.</span></span> <span data-ttu-id="e4b72-259">記録はファイルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="e4b72-260">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="e4b72-260">Mixed Reality Capture</span></span>

<span data-ttu-id="e4b72-261">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="e4b72-262">混合の現実ファイルをデバイスからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e4b72-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="e4b72-263">ストリーミングには op = stream クエリパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="e4b72-264">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-264">Parameters</span></span>
* <span data-ttu-id="e4b72-265">filename: 取得するビデオファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="e4b72-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="e4b72-266">op: ストリーム</span><span class="sxs-lookup"><span data-stu-id="e4b72-266">op : stream</span></span>

<span data-ttu-id="e4b72-267">**/api/holographic/mrc/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="e4b72-268">デバイスから mixed reality の記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="e4b72-269">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-269">Parameters</span></span>
* <span data-ttu-id="e4b72-270">filename: 削除するファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="e4b72-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="e4b72-271">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="e4b72-272">デバイスに格納されている mixed reality ファイルの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="e4b72-273">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="e4b72-274">Mixed reality の写真を取得し、デバイスにファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="e4b72-275">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-275">Parameters</span></span>
* <span data-ttu-id="e4b72-276">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-277">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-278">RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="e4b72-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="e4b72-279">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="e4b72-280">既定の mixed reality キャプチャ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="e4b72-281">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="e4b72-282">既定の mixed reality キャプチャ設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="e4b72-283">これらの設定の一部は、システムの MRC の写真とビデオキャプチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="e4b72-284">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="e4b72-285">Windows デバイスポータル内の mixed reality キャプチャの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="e4b72-286">***Response***</span><span class="sxs-lookup"><span data-stu-id="e4b72-286">***Response***</span></span>

<span data-ttu-id="e4b72-287">応答には、Windows デバイスポータルがビデオを記録しているかどうかを示す JSON プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4b72-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="e4b72-288">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="e4b72-289">指定したファイルのサムネイルイメージを取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="e4b72-290">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-290">Parameters</span></span>
* <span data-ttu-id="e4b72-291">filename: サムネイルが要求されているファイルの名前 (hex64 encoded)</span><span class="sxs-lookup"><span data-stu-id="e4b72-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="e4b72-292">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="e4b72-293">Mixed reality の記録を開始します</span><span class="sxs-lookup"><span data-stu-id="e4b72-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="e4b72-294">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-294">Parameters</span></span>
* <span data-ttu-id="e4b72-295">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-296">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-297">mic: キャプチャマイク: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-298">ループバック: キャプチャアプリオーディオ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-299">RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="e4b72-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="e4b72-300">vstab: (HoloLens 2 のみ) ビデオ安定化を有効にします。 true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="e4b72-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="e4b72-301">vstabbuffer: (HoloLens 2 のみ) ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定値は15フレーム)</span><span class="sxs-lookup"><span data-stu-id="e4b72-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="e4b72-302">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="e4b72-303">現在の mixed reality 記録を停止します</span><span class="sxs-lookup"><span data-stu-id="e4b72-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="e4b72-304">Mixed Reality ストリーミング</span><span class="sxs-lookup"><span data-stu-id="e4b72-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="e4b72-305">HoloLens は、フラグメント化された mp4 のチャンクダウンロードを使用して、混合現実のライブプレビューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e4b72-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="e4b72-306">混合現実のストリームは、キャプチャ対象を制御するために、同じパラメーターのセットを共有します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="e4b72-307">holo: キャプチャホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="e4b72-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="e4b72-308">pv: キャプチャの PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="e4b72-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="e4b72-309">mic: マイクのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="e4b72-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="e4b72-310">ループバック: アプリオーディオのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="e4b72-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="e4b72-311">これらのいずれも指定されていない場合、ホログラム、photo/video カメラ、アプリオーディオがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="e4b72-312">指定されている場合: 未指定のパラメーターは既定で false に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="e4b72-313">省略可能なパラメーター (HoloLens 2 のみ)</span><span class="sxs-lookup"><span data-stu-id="e4b72-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="e4b72-314">RenderFromCamera: 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="e4b72-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="e4b72-315">vstab: ビデオ安定化を有効にします。 true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="e4b72-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="e4b72-316">vstabbuffer: ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定では15フレーム)</span><span class="sxs-lookup"><span data-stu-id="e4b72-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="e4b72-317">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="e4b72-318">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="e4b72-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="e4b72-319">**/api/holographic/stream/live_high. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="e4b72-320">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="e4b72-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="e4b72-321">**/api/holographic/stream/live_med. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="e4b72-322">854x480p 30 fps 2.5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="e4b72-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="e4b72-323">**/api/holographic/stream/live_low. mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="e4b72-324">428x240p 15fps 0.6 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="e4b72-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="e4b72-325">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="e4b72-325">Networking</span></span>

<span data-ttu-id="e4b72-326">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="e4b72-327">現在の ip 構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="e4b72-328">OS 情報</span><span class="sxs-lookup"><span data-stu-id="e4b72-328">OS Information</span></span>

<span data-ttu-id="e4b72-329">**/api/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="e4b72-330">オペレーティングシステム情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-330">Gets operating system information</span></span>

<span data-ttu-id="e4b72-331">**/api/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="e4b72-332">コンピューター名を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-332">Gets the machine name</span></span>

<span data-ttu-id="e4b72-333">**/api/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="e4b72-334">コンピューター名を設定します</span><span class="sxs-lookup"><span data-stu-id="e4b72-334">Sets the machine name</span></span>

<span data-ttu-id="e4b72-335">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-335">Parameters</span></span>
* <span data-ttu-id="e4b72-336">[名前]: 新しいコンピューター名、hex64 encoded、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="e4b72-337">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="e4b72-337">Performance data</span></span>

<span data-ttu-id="e4b72-338">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="e4b72-339">詳細を含む実行中のプロセスの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="e4b72-340">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-340">Return data</span></span>
* <span data-ttu-id="e4b72-341">各プロセスのプロセスと詳細の一覧を含む JSON</span><span class="sxs-lookup"><span data-stu-id="e4b72-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="e4b72-342">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="e4b72-343">システムパフォーマンス統計情報 (i/o 読み取り/書き込み、メモリ統計など) を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="e4b72-344">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-344">Return data</span></span>
* <span data-ttu-id="e4b72-345">システム情報を含む JSON: CPU、GPU、メモリ、ネットワーク、IO</span><span class="sxs-lookup"><span data-stu-id="e4b72-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="e4b72-346">Power</span><span class="sxs-lookup"><span data-stu-id="e4b72-346">Power</span></span>

<span data-ttu-id="e4b72-347">**/api/バッテリ (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="e4b72-348">現在のバッテリの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-348">Gets the current battery state</span></span>

<span data-ttu-id="e4b72-349">**//(GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="e4b72-350">システムが低電力状態であるかどうかを確認します</span><span class="sxs-lookup"><span data-stu-id="e4b72-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="e4b72-351">リモート コントロール</span><span class="sxs-lookup"><span data-stu-id="e4b72-351">Remote Control</span></span>

<span data-ttu-id="e4b72-352">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="e4b72-353">ターゲットデバイスを再起動します</span><span class="sxs-lookup"><span data-stu-id="e4b72-353">Restarts the target device</span></span>

<span data-ttu-id="e4b72-354">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="e4b72-355">ターゲットデバイスをシャットダウンします</span><span class="sxs-lookup"><span data-stu-id="e4b72-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="e4b72-356">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="e4b72-356">Task Manager</span></span>

<span data-ttu-id="e4b72-357">**/api/taskmanager/app (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="e4b72-358">モダンアプリを停止します</span><span class="sxs-lookup"><span data-stu-id="e4b72-358">Stops a modern app</span></span>

<span data-ttu-id="e4b72-359">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-359">Parameters</span></span>
* <span data-ttu-id="e4b72-360">パッケージ: アプリパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="e4b72-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="e4b72-361">forcestop: すべてのプロセスを強制的に停止します (= yes)</span><span class="sxs-lookup"><span data-stu-id="e4b72-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="e4b72-362">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="e4b72-363">モダンアプリを開始します</span><span class="sxs-lookup"><span data-stu-id="e4b72-363">Starts a modern app</span></span>

<span data-ttu-id="e4b72-364">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-364">Parameters</span></span>
* <span data-ttu-id="e4b72-365">appid: アプリの開始、hex64 エンコード</span><span class="sxs-lookup"><span data-stu-id="e4b72-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="e4b72-366">パッケージ: アプリパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="e4b72-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="e4b72-367">WiFi の管理</span><span class="sxs-lookup"><span data-stu-id="e4b72-367">WiFi Management</span></span>

<span data-ttu-id="e4b72-368">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="e4b72-369">ワイヤレスネットワークインターフェイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="e4b72-370">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-370">Return data</span></span>
* <span data-ttu-id="e4b72-371">詳細 (GUID、説明など) があるワイヤレスインターフェイスの一覧</span><span class="sxs-lookup"><span data-stu-id="e4b72-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="e4b72-372">**/api/wifi/network (削除)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="e4b72-373">指定したインターフェイスのネットワークに関連付けられているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="e4b72-374">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-374">Parameters</span></span>
* <span data-ttu-id="e4b72-375">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="e4b72-375">interface : network interface guid</span></span>
* <span data-ttu-id="e4b72-376">プロファイル: プロファイル名</span><span class="sxs-lookup"><span data-stu-id="e4b72-376">profile : profile name</span></span>

<span data-ttu-id="e4b72-377">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="e4b72-378">指定されたネットワークインターフェイスのワイヤレスネットワークを列挙します</span><span class="sxs-lookup"><span data-stu-id="e4b72-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="e4b72-379">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-379">Parameters</span></span>
* <span data-ttu-id="e4b72-380">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="e4b72-380">interface : network interface guid</span></span>

<span data-ttu-id="e4b72-381">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-381">Return data</span></span>
* <span data-ttu-id="e4b72-382">ネットワークインターフェイスで検出されたワイヤレスネットワークの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="e4b72-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="e4b72-383">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="e4b72-384">指定されたインターフェイスでネットワークに接続または切断します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="e4b72-385">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-385">Parameters</span></span>
* <span data-ttu-id="e4b72-386">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="e4b72-386">interface : network interface guid</span></span>
* <span data-ttu-id="e4b72-387">ssid: 接続先の ssid、hex64 encoded、</span><span class="sxs-lookup"><span data-stu-id="e4b72-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="e4b72-388">op: 接続または切断</span><span class="sxs-lookup"><span data-stu-id="e4b72-388">op : connect or disconnect</span></span>
* <span data-ttu-id="e4b72-389">createprofile: はいまたはいいえ</span><span class="sxs-lookup"><span data-stu-id="e4b72-389">createprofile : yes or no</span></span>
* <span data-ttu-id="e4b72-390">キー: shared key、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="e4b72-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="e4b72-391">Windows パフォーマンス レコーダー</span><span class="sxs-lookup"><span data-stu-id="e4b72-391">Windows Performance Recorder</span></span>

<span data-ttu-id="e4b72-392">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="e4b72-393">WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="e4b72-394">ペイロード</span><span class="sxs-lookup"><span data-stu-id="e4b72-394">Payload</span></span>
* <span data-ttu-id="e4b72-395">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="e4b72-395">multi-part conforming http body</span></span>

<span data-ttu-id="e4b72-396">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-396">Return data</span></span>
* <span data-ttu-id="e4b72-397">WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-397">Returns the WPR session status.</span></span>

<span data-ttu-id="e4b72-398">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="e4b72-399">WPR セッションの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="e4b72-400">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-400">Return data</span></span>
* <span data-ttu-id="e4b72-401">WPR セッションの状態。</span><span class="sxs-lookup"><span data-stu-id="e4b72-401">WPR session status.</span></span>

<span data-ttu-id="e4b72-402">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="e4b72-403">WPR (パフォーマンス) トレースセッションを停止します</span><span class="sxs-lookup"><span data-stu-id="e4b72-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="e4b72-404">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-404">Return data</span></span>
* <span data-ttu-id="e4b72-405">トレース ETL ファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-405">Returns the trace ETL file</span></span>

<span data-ttu-id="e4b72-406">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="e4b72-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="e4b72-407">WPR (パフォーマンス) トレースセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="e4b72-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="e4b72-408">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4b72-408">Parameters</span></span>
* <span data-ttu-id="e4b72-409">プロファイル: プロファイル名。</span><span class="sxs-lookup"><span data-stu-id="e4b72-409">profile : Profile name.</span></span> <span data-ttu-id="e4b72-410">使用可能なプロファイルは perfprofiles/profiles. json に格納されます。</span><span class="sxs-lookup"><span data-stu-id="e4b72-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="e4b72-411">データを返します</span><span class="sxs-lookup"><span data-stu-id="e4b72-411">Return data</span></span>
* <span data-ttu-id="e4b72-412">開始時に、WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="e4b72-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4b72-413">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4b72-413">See also</span></span>
* [<span data-ttu-id="e4b72-414">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="e4b72-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="e4b72-415">デバイスポータルコア API リファレンス (UWP)</span><span class="sxs-lookup"><span data-stu-id="e4b72-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
