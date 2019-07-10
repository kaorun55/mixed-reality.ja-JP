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
# <a name="device-portal-api-reference"></a>デバイス ポータル API リファレンス

内のすべて、 [Windows Device Portal](using-the-windows-device-portal.md)データにアクセスし、デバイスの管理をプログラム的に使用できる REST API の上に構築されます。

## <a name="app-deloyment"></a>アプリの展開

**/api/app/packagemanager/package (削除)**

アプリをアンインストールします。

Parameters
* パッケージ:アンインストールするパッケージのファイル名。

**/api/app/packagemanager/package (POST)**

アプリをインストールします。

Parameters
* パッケージ:パッケージをインストールするのファイル名。

ペイロード
* 準拠したマルチパートの http 本文

**/api/app/packagemanager/packages (GET)**

詳細と、システムにインストールされているアプリの一覧を取得します。

戻り値のデータ
* 詳細とインストールされているパッケージの一覧

**/api/app/packagemanager/state (GET)**

アプリのインストールの進行状況での状態を取得します。

## <a name="dump-collection"></a>ダンプの収集

**/api/debug/dump/usermode/crashcontrol (削除)**

サイドロードされたアプリのダンプの収集がクラッシュする無効にします。

Parameters
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashcontrol (GET)**

クラッシュ ダンプの収集にサイドロードしたアプリの設定を取得します。

Parameters
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashcontrol (POST)**

有効にし、サイドロードされたアプリのダンプ制御の設定の設定

Parameters
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashdump (削除)**

サイドロードされたアプリのクラッシュ ダンプを削除します。

Parameters
* packageFullname: パッケージ名
* ファイル名: ダンプ ファイルの名前

**/api/debug/dump/usermode/crashdump (GET)**

サイドロードされたアプリのクラッシュ ダンプを取得します。

Parameters
* packageFullname: パッケージ名
* ファイル名: ダンプ ファイルの名前

戻り値のデータ
* ダンプ ファイル。 WinDbg または Visual Studio での検査します。

**/api/debug/dump/usermode/dumps (GET)**

サイドロードしたアプリのすべてのクラッシュ ダンプのリストを返します

戻り値のデータ
* サイド ロード アプリごとの一連のクラッシュ ダンプします。

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

登録されているプロバイダーを列挙します。

戻り値のデータ
* プロバイダー、フレンドリ名と GUID の一覧

**/api/etw/session/realtime (GET/WebSocket)**

リアルタイムの ETW セッションを作成します。websocket 経由で管理します。

戻り値のデータ
* 有効なプロバイダーから ETW イベント

## <a name="holographic-os"></a>ホログラフィック OS

**/api/holographic/os/etw/customproviders (GET)**

システムに登録されていない HoloLens 特定 ETW プロバイダーの一覧を返します

**/api/holographic/os/services (GET)**

実行されているすべてのサービスの状態を返します。

**/api/holographic/os/settings/ipd (GET)**

ミリメートル単位ストアド IPD (Interpupillary 距離) を取得します。

**/api/holographic/os/settings/ipd (POST)**

IPD を設定します。

Parameters
* ipd:ミリメートル単位で設定される新しい IPD 値

**/api/holographic/os/webmanagement/settings/https (GET)**

Device Portal の HTTPS 要件を取得する

**/api/holographic/os/webmanagement/settings/https (POST)**

デバイスのポータルの HTTPS 要件を設定します。

Parameters
* 必須: yes、no または既定値

## <a name="holographic-perception"></a>Holographic Perception

**/api/holographic/perception/client (GET/WebSocket)**

Websocket のアップグレードを受け取り、30 fps で更新プログラムを送信する perception クライアントを実行します。

Parameters
* clientmode:"active"強制的 visual 追跡モード受動的に確立されることはできません

## <a name="holographic-thermal"></a>Holographic 温度

**/api/holographic/thermal/stage (GET)**

(通常 0、1 ウォーム、重要な 2) のデバイスの温度のステージを取得します。

## <a name="perception-simulation-control"></a>Perception シミュレーション コントロール

**/api/holographic/simulation/control/mode (GET)**

シミュレーションのモードを取得します。

**/api/holographic/simulation/control/mode (POST)**

シミュレーションのモードを設定します。

Parameters
* モード: シミュレーション モード: 既定では、シミュレーション、リモートのレガシ

**/api/holographic/simulation/control/stream (削除)**

コントロールのストリームを削除します。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

コントロールのストリームの web ソケット接続を開きます。

**/api/holographic/simulation/control/stream (POST)**

コントロールのストリームを作成する (優先度が必要) または作成されたストリーム (必要な streamId) にデータをポストします。 ポストされたデータは、' アプリケーションまたはオクテット ストリーム ' 型のことが必要です。

## <a name="perception-simulation-playback"></a>Perception シミュレーションの再生

**/api/holographic/simulation/playback/file (削除)**

録画を削除します。

Parameters
* 録音:削除する記録の名前です。

**/api/holographic/simulation/playback/file (POST)**

録画をアップロードします。

**/api/holographic/simulation/playback/files (GET)**

すべての記録を取得します。

**/api/holographic/simulation/playback/session (GET)**

録画の現在の再生状態を取得します。

Parameters
* 録音:記録の名前です。

**/api/holographic/simulation/playback/session/file (削除)**

録画をアンロードします。

Parameters
* 録音:アンロードする記録の名前です。

**/api/holographic/simulation/playback/session/file (POST)**

録画を読み込みます。

Parameters
* 録音:記録を読み込むの名前です。

**/api/holographic/simulation/playback/session/files (GET)**

読み込まれたすべての記録を取得します。

**/api/holographic/simulation/playback/session/pause (POST)**

記録を一時停止します。

Parameters
* 録音:記録の名前です。

**/api/holographic/simulation/playback/session/play (POST)**

記録を再生します。

Parameters
* 録音:記録の名前です。

**/api/holographic/simulation/playback/session/stop (POST)**

録画を停止します。

Parameters
* 録音:記録の名前です。

**/api/holographic/simulation/playback/session/types (GET)**

読み込まれた記録では、データの種類を取得します。

Parameters
* 録音:記録の名前です。

## <a name="perception-simulation-recording"></a>Perception シミュレーションの記録

**/api/holographic/simulation/recording/start (POST)**

録画を開始します。 1 つの記録のみを一度にアクティブにできます。 Head、手、spatialMapping または環境のいずれかを設定する必要があります。

Parameters
* ヘッド:レコード ヘッド データを 1 に設定します。
* ハンズ:1 に設定するには手の形のデータを記録します。
* spatialMapping:空間マッピングを記録する、1 に設定します。
* 環境:環境のデータを記録する、1 に設定します。
* 名:記録の名前です。
* singleSpatialMappingFrame:空間マッピングは 1 つのフレームのみを記録する、1 に設定します。

**/api/holographic/simulation/recording/status (GET)**

状態の記録を取得します。

**/api/holographic/simulation/recording/stop (GET)**

現在の記録を停止します。 記録は、ファイルとして返されます。

## <a name="mixed-reality-capture"></a>Mixed Reality キャプチャ

**/api/holographic/mrc/file (GET)**

デバイスから複合現実ファイルをダウンロードします。 使用 op ストリーミング ストリームのクエリ パラメーターを = です。

Parameters
* ファイル名:取得するビデオ ファイルのエンコード、名前、hex64
* op: ストリーム

**/api/holographic/mrc/file (削除)**

デバイスから録画複合現実を削除します。

Parameters
* ファイル名:削除するファイルのエンコード、名前、hex64

**/api/holographic/mrc/files (GET)**

デバイスに保存された複合現実ファイルの一覧を返します

**/api/holographic/mrc/photo (POST)**

複合現実の写真を撮影し、デバイス上のファイルを作成します

Parameters
* holo: キャプチャ ホログラム: true または false (既定値は false)
* pv: キャプチャ PV カメラ: true または false (既定値は false)
* RenderFromCamera:写真/ビデオのカメラの観点からレンダリングを (HoloLens 2 のみ): true または false (既定値は true)

**/api/holographic/mrc/settings (GET)**

取得、既定値に、複合現実設定のキャプチャ

**/api/holographic/mrc/settings (POST)**

セットの既定値に、複合現実設定のキャプチャ。  これらの設定の一部は、システムの MRC 写真とビデオのキャプチャに適用されます。

**/api/holographic/mrc/status (GET)**

記録された複合現実 (実行、停止) の状態を取得します。

**/api/holographic/mrc/thumbnail (GET)**

指定したファイルのサムネイル画像を取得します。

Parameters
* ファイル名:エンコードされる場合は、サムネイルを要求する対象のファイルの名前、hex64

**/api/holographic/mrc/video/control/start (POST)**

複合現実の録音を開始します。

Parameters
* holo: キャプチャ ホログラム: true または false (既定値は false)
* pv: キャプチャ PV カメラ: true または false (既定値は false)
* mic: キャプチャ マイク: true または false (既定値は false)
* ループバック: アプリの音声のキャプチャ: true または false (既定値は false)
* RenderFromCamera:写真/ビデオのカメラの観点からレンダリングを (HoloLens 2 のみ): true または false (既定値は true)
* vstab:有効にするビデオ安定化の (HoloLens 2 のみ): true または false (既定値は true)
* vstabbuffer:ビデオ安定化バッファーの待機時間を (HoloLens 2 のみ):0 ~ 30 フレーム (既定値は 15 フレーム)

**/api/holographic/mrc/video/control/stop (POST)**

停止現在混合現実の記録

## <a name="mixed-reality-streaming"></a>複合現実のストリーミング

HoloLens では、フラグメント化 mp4 のチャンクのダウンロードを使用して複合現実のライブ プレビューをサポートします。

複合現実のストリームは、キャプチャされるものを制御するパラメーターの同じセットを共有します。
* holo: キャプチャ ホログラム: true または false
* pv: キャプチャ PV カメラ: true または false
* mic: キャプチャ マイク: true または false
* ループバック: アプリの音声のキャプチャ: true または false

指定しないと、これらの場合: ホログラム、カメラの写真とビデオ、およびアプリの音声がキャプチャします。<br>
指定されている場合: 指定されていないパラメーターは既定で false

省略可能なパラメーター (HoloLens 2 のみ)
* RenderFromCamera: 写真/ビデオのカメラの観点からを表示: true または false (既定値は true)
* vstab: ビデオ安定化を有効にする: true または false (既定値は false)
* vstabbuffer: ビデオ安定化バッファーの待機時間。0 ~ 30 フレーム (既定値は 15 フレーム)

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30 fps 5Mbit ストリーム。

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30 fps 5Mbit ストリーム。

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30 fps 2.5Mbit ストリーム。

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15 fps 0.6Mbit ストリーム。

## <a name="networking"></a>ネットワーク

**/api/networking/ipconfig (GET)**

現在の ip 構成を取得します。

## <a name="os-information"></a>OS 情報

**/api/os/info (GET)**

オペレーティング システムの情報を取得します。

**/api/os/machinename (GET)**

コンピューター名を取得します。

**/api/os/machinename (POST)**

コンピューター名を設定します。

Parameters
* 名:新しいコンピューター名、hex64 エンコードされる場合に設定するには

## <a name="performance-data"></a>パフォーマンス データ

**/api/resourcemanager/processes (GET)**

詳細でプロセスを実行の一覧を返します

戻り値のデータ
* プロセスと各プロセスの詳細の一覧が JSON

**/api/resourcemanager/systemperf (GET)**

(読み取り/書き込みの I/O、メモリの統計情報などシステム パフォーマンスの統計情報を返しますです。

戻り値のデータ
* システム情報を使用して、JSON:CPU、GPU、メモリ、ネットワーク、IO

## <a name="power"></a>Power

**/api/power/battery (GET)**

現在のバッテリの状態を取得します。

**/api/power/state (GET)**

システムの低電力状態を確認します

## <a name="remote-control"></a>リモート コントロール

**/api/control/restart (POST)**

ターゲット デバイスを再起動します。

**/api/control/shutdown (POST)**

ターゲット デバイスをシャット ダウン

## <a name="task-manager"></a>タスク マネージャー

**/api/taskmanager/app (削除)**

最新のアプリを停止します。

Parameters
* パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前
* 強制:強制的にすべてのプロセスを停止する (= [はい])

**/api/taskmanager/app (POST)**

最新のアプリを起動します。

Parameters
* appid:開始するアプリの PRAID、hex64 エンコード
* パッケージ:エンコードされた hex64、アプリ パッケージの完全な名前

## <a name="wifi-management"></a>WiFi の管理

**/api/wifi/interfaces (GET)**

ワイヤレス ネットワーク インターフェイスを列挙します。

戻り値のデータ
* (GUID、説明など) の詳細を含むワイヤレス インターフェイスの一覧

**/api/wifi/network (削除)**

指定されたインターフェイス上のネットワークに関連付けられているプロファイルを削除します。

Parameters
* インターフェイス: ネットワーク インターフェイスの guid
* プロファイル: プロファイル名

**/api/wifi/networks (GET)**

指定したネットワーク インターフェイス上でワイヤレス ネットワークを列挙します。

Parameters
* インターフェイス: ネットワーク インターフェイスの guid

戻り値のデータ
* ネットワーク インターフェイスの詳細に検出されたワイヤレス ネットワークの一覧

**/api/wifi/network (POST)**

接続または指定されたインターフェイス上のネットワークに接続を切断

Parameters
* インターフェイス: ネットワーク インターフェイスの guid
* ssid: ssid、hex64 への接続にエンコードします。
* op: 接続または切断
* createprofile: はいまたは no
* キー: エンコードされた共有のキー、hex64

## <a name="windows-performance-recorder"></a>Windows パフォーマンス レコーダー

**/api/wpr/customtrace (POST)**

WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。

ペイロード
* 準拠したマルチパートの http 本文

戻り値のデータ
* WPR セッションの状態を返します。

**/api/wpr/status (GET)**

WPR セッションの状態を取得します。

戻り値のデータ
* WPR セッションの状態。

**/api/wpr/trace (GET)**

WPR (パフォーマンス) のトレース セッションを停止します。

戻り値のデータ
* トレース ETL ファイルを返します

**/api/wpr/trace (POST)**

セッションのトレース WPR (パフォーマンス) を開始します。

Parameters
* プロファイル:プロファイルの名前。 使用可能なプロファイル perfprofiles/profiles.json に格納されます。

戻り値のデータ
* 起動時に、WPR セッションの状態を返します。

## <a name="see-also"></a>関連項目
* [Windows Device Portal を使用する](using-the-windows-device-portal.md)
* [デバイス ポータル core API リファレンス (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
