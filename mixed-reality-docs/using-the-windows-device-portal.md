---
title: Windows デバイスポータルの使用
description: HoloLens 用 Windows デバイスポータルでは、Wi-fi または USB を使用してデバイスをリモートで構成および管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイスポータルには、HoloLens を管理し、アプリをデバッグおよび最適化するのに役立つ多くのツールが用意されています。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows デバイスポータル、HoloLens
ms.openlocfilehash: 43ecfead7d2882d3624809bc05184f74131b8594
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375789"
---
# <a name="using-the-windows-device-portal"></a>Windows デバイスポータルの使用

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> Windows デバイス ポータル</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens 用 Windows デバイスポータルでは、Wi-fi または USB を使用してデバイスをリモートで構成および管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイスポータルには、HoloLens を管理し、アプリをデバッグおよび最適化するのに役立つ多くのツールが用意されています。

このドキュメントは、具体的には HoloLens 用の Windows デバイスポータルに関するものです。 デスクトップ用 Windows デバイスポータル (Windows Mixed Reality を含む) を使用するには、「 [Windows デバイスポータルの概要](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)」を参照してください。

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Windows デバイスポータルを使用するための HoloLens の設定

1. HoloLens の電源を入れ、デバイスを装着します。
2. HoloLens (第1世代) の HoloLens2 または[ブルーム](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)の[開始ジェスチャ](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)を実行して、メインメニューを起動します。 
3. **[設定]** タイルを見つめ、hololens (第1世代) での[エアタップ](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)ジェスチャを実行するか、[または、接しているか、またはハンドレイを使用](https://docs.microsoft.com/hololens/hololens2-basic-usage)して hololens 2 で選択します。 
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[Developer Mode]** (開発者モード) を有効にします。
7. [下へスクロール](gaze-and-commit.md#composite-gestures)し、**デバイスポータル**を有効にします。
8. USB または Wi-fi 経由でこの HoloLens にアプリを展開できるように Windows デバイスポータルを設定する場合は、 **[ペアリング] をクリック**して[ペアリングピンを生成](using-visual-studio.md)します。 最初のデプロイ中に Visual Studio に PIN を入力するまでは、ピンポップアップで設定アプリをそのままにしておきます。

   ![Windows Holographic の設定アプリで開発者モードを有効にする](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Wi-fi 経由の接続

1. [HoloLens を wi-fi に接続](connecting-to-wi-fi-on-hololens.md)します。
2. デバイスの IP アドレスを検索します。
   * > 設定 の **ネットワーク & インターネット > wi-fi > 詳細オプション** で、デバイスの IP アドレスを検索します。
3. PC の web ブラウザーから、 https://< YOUR_HOLOLENS_IP_ADDRESS にアクセスし >
   * ブラウザーに次のメッセージが表示されます。"この web サイトのセキュリティ証明書に問題があります"。 これは、Device Portal に発行された証明書がテスト証明書であるためです。 ここでは、この証明書エラーを無視して続行できます。

## <a name="connecting-over-usb"></a>USB 経由の接続

1. Windows 10 developer tools が PC にインストールされていることを確認するため[のツールをインストール](install-the-tools.md)します。 これで USB 接続が有効になります。
2. Hololens のマイクロ USB ケーブルまたは hololens 2 用の USB-C を使用して、HoloLens を PC に接続します。
3. PC の web ブラウザーから、 [https://127.0.0.1:10080](https://127.0.0.1:10080)にアクセスします。

## <a name="connecting-to-an-emulator"></a>エミュレーターへの接続

Device Portal はエミュレーターで使うこともできます。 デバイスポータルに接続するには、[ツールバー](using-the-hololens-emulator.md)を使用します。 次のアイコンをクリックします。デバイスポータルアイコンを開いて ![**デバイスポータルを開く**には](images/emulator-deviceportal.png) 次のようにします。エミュレーターで HoloLens OS の Windows デバイス ポータルを開きます。

## <a name="creating-a-username-and-password"></a>ユーザー名とパスワードの作成

Windows デバイスポータルへのアクセスをセットアップ ![](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows デバイスポータルへのアクセスをセットアップする*

HoloLens で初めて Device Portal に接続するときは、ユーザー名とパスワードを作成する必要があります。
1. PC 上の Web ブラウザーで、HoloLens の IP アドレスを入力します。 [Set up access] (アクセスのセットアップ) ページが開きます。
2. [Pin の**要求**] をクリックまたはタップし、HoloLens ディスプレイを見て、生成された pin を取得します。
3. **[デバイスに表示される pin** ] ボックスに pin を入力します。
4. Device Portal への接続に使うユーザー名を入力します。 Microsoft アカウント (MSA) 名やドメイン アカウント名を指定する必要はありません。
5. パスワードを入力し、確認用にもう一度入力します。 パスワードは 7 文字以上にする必要があります。 MSA やドメインのパスワードと同じにする必要はありません。
6. **[ペアリング]** をクリックして、HoloLens の Windows デバイスポータルに接続します。

このユーザー名またはパスワードをいつでも変更する場合は、[デバイスのセキュリティ] ページにアクセスして、[https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.] に移動し、このプロセスを繰り返すことができます。

## <a name="security-certificate"></a>セキュリティ証明書

ブラウザーに "証明書エラー" が表示された場合は、デバイスとの信頼関係を作成することで修正できます。

ぞれぞれの HoloLens では、SSL 接続用に一意の自己署名証明書が生成されます。 既定では、この証明書が PC の Web ブラウザーによって信頼されていないため、"証明書エラー" が発生することがあります。 この証明書を HoloLens から (USB または信頼している Wi-Fi ネットワーク経由で) ダウンロードし、PC で信頼すると、デバイスに安全に接続できます。
1. **セキュリティで保護されたネットワーク (USB または信頼できる Wi-fi ネットワーク) を使用していることを確認します。**
2. デバイスポータルの [セキュリティ] ページから、このデバイスの証明書をダウンロードします。
   * 移動: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
   * システム > の基本設定のノードを開きます。 
   * [デバイスのセキュリティ] まで下にスクロールし、[このデバイスの証明書をダウンロードします] ボタンをクリックします。
3. PC の "信頼されたルート証明機関" ストアに証明書をインストールします。
   * Windows のメニューから、次のように入力します。コンピューターの証明書を管理し、アプレットを開始します。
   * **[信頼されたルート証明機関]** フォルダーを展開します。
   * **[証明書]** フォルダーをクリックします。
   * [操作] メニューで、次のように選択します。インポート > すべてのタスク...
   * Device Portal からダウンロードした証明書ファイルを使って、証明書のインポート ウィザードを完了します。
4. ブラウザーを再起動します。

>[!NOTE]
> この証明書はデバイスに対してのみ信頼されるため、デバイスがフラッシュされた場合、ユーザーはプロセスを再度実行する必要があります。


## <a name="device-portal-pages"></a>Device Portal のページ

### <a name="home"></a>ホーム (Home)

Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png) で Windows デバイスポータルのホームページを ![する<br>
*Microsoft HoloLens の Windows デバイスポータルホームページ*

Device Portal セッションは Home (ホーム) ページから始まります。 他のページにアクセスするには、ホーム ページの左側にあるナビゲーション バーを使います。

ページの最上部にあるツール バーでは、よく使われる状態や機能にアクセスできます。
* **オンライン**:デバイスが Wi-fi に接続されているかどうかを示します。
* **シャットダウン**:デバイスをオフにします。
* **再起動**:デバイスの電源を入れます。
* **セキュリティ**:[デバイスのセキュリティ] ページを開きます。
* **クール**:デバイスの温度を示します。
* **A/C**:デバイスが電源に接続され、充電されているかどうかを示します。
* **ヘルプ**:REST インターフェイスのドキュメントページを開きます。

ホーム ページには次の情報が表示されます。
* **デバイスの状態:** デバイスの正常性を監視し、重大なエラーを報告します。
* **Windows 情報:** HoloLens の名前と、現在インストールされている windows のバージョンが表示されます。
* **[Preferences]** (設定) セクションには次の設定が含まれます。
   * **IPD**:Interpupillary distance (IPD) を設定します。これは、ユーザーの pupils の中心との間の距離 (ミリメートル単位) を示します。 設定はすぐに反映されます。 既定値は、デバイスのセットアップ時に自動的に計算された値です。
   * **デバイス名**:HoloLens に名前を割り当てます。 この値を変更した場合、変更を有効にするにはデバイスを再起動する必要があります。 **[保存]** をクリックすると、すぐにデバイスを再起動するか、後で再起動するかを確認するダイアログが表示されます。
   * **スリープ設定**:デバイスが電源に接続されているとき、およびバッテリが稼働しているときに、デバイスがスリープ状態になるまでの待機時間を設定します。

### <a name="3d-view"></a>3D View (3D ビュー)

Microsoft HoloLens](images/3dview-1000px.png) の Windows デバイスポータルの ![3D ビューページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [3D ビュー] ページ*

[3D View] (3D ビュー) ページを使うと、HoloLens がどのように周囲を解釈するかを確認できます。 ビュー内を移動するには、マウスを次のように使います。
* 回転: 左クリック + マウス
* パン: 右クリック + マウス;
* Zoom: マウスのスクロール。
* **追跡オプション**
   * **[ビジュアル追跡の強制]** チェックボックスをオンにして、継続的なビジュアル追跡を有効にします。 
   * **Pause**は、ビジュアルの追跡を停止します。
* **表示オプション**:3D ビューのオプションを設定します。
  * **追跡**:ビジュアルの追跡がアクティブかどうかを示します。
  * **フロアの表示**:チェッカーフロア平面を表示します。
  * **視錐台を表示**:視錐のビューを表示します。
  * **安定化平面の表示**:HoloLens が安定化運動に使用する平面を表示します。
  * **メッシュの表示**:周囲を表す空間マッピングメッシュが表示されます。
  * **空間アンカーの表示**:アクティブなアプリの空間アンカーを表示します。 アンカーを取得して更新するには、[更新] ボタンをクリックする必要があります。
  * **詳細の表示**:リアルタイムで変更されるときに、手の位置、頭の回転の四元数、およびデバイスのオリジンベクターを表示します。
  * **全画面表示ボタン**:3D ビューを全画面表示モードで表示します。 Esc キーを押すと全画面表示を終了します。
* **Surface**の再構築: **[更新]** をクリックまたはタップして、デバイスから最新の空間マッピングメッシュを表示します。 完全なパスは、完了するまでに時間がかかる場合があります (最大で数秒)。 メッシュは3D ビューで自動的に更新されません。また、 **[更新]** を手動でクリックして、デバイスから最新のメッシュを取得する必要があります。 **[保存]** をクリックして、現在の空間マッピングメッシュを PC 上の obj ファイルとして保存します。
* **空間アンカー**:アクティブなアプリの空間アンカーを表示または更新するには、[更新] をクリックします。

### <a name="mixed-reality-capture"></a>Mixed Reality キャプチャ

Microsoft HoloLens の Windows デバイスポータルで Mixed Reality キャプチャページを ![する](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens の Windows デバイスポータルの混合現実のキャプチャページ*

Mixed Reality キャプチャ ページを使うと、HoloLens からメディア ストリームを保存できます。
* **設定**:次の設定を確認して、キャプチャされるメディアストリームを制御します。
  * **ホログラム**:ビデオストリームの holographic コンテンツをキャプチャします。 ホログラムは、ステレオではなくモノラルでレンダリングされます。
  * **PV カメラ**:写真/ビデオカメラからビデオストリームをキャプチャします。
  * **Mic オーディオ**:マイク配列からオーディオをキャプチャします。
  * **アプリオーディオ**:現在実行中のアプリからオーディオをキャプチャします。
  * **カメラからのレンダリング**:[実行中のアプリでサポートされ](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)ている場合 (HoloLens 2 のみ)、写真/ビデオカメラの観点からキャプチャを配置します。
  * **ライブプレビューの品質**:ライブプレビューの画面の解像度、フレームレート、およびストリーミングレートを選択します。
* **[ライブプレビュー]** ボタンをクリックまたはタップして、キャプチャストリームを表示します。 **ライブプレビューの停止**、キャプチャストリームを停止します。
* **[記録]** をクリックまたはタップして、指定した設定を使用して mixed reality ストリームの記録を開始します。 **[記録の停止]** は、記録を終了して保存します。
* キャプチャストリームから静止画像を撮影するには、 **[写真の撮影]** をクリックまたはタップします。
* **ビデオと写真**:デバイスで撮影されたビデオと写真のキャプチャの一覧が表示されます。

> [!NOTE]
> [同時に MRC に](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)は、次のような制限があります。
> * Windows デバイスポータルがビデオを記録しているときに、アプリが写真/ビデオカメラにアクセスしようとすると、ビデオの記録が停止します。
>   * アプリが SharedReadOnly モードで写真/ビデオカメラにアクセスした場合、HoloLens 2 はビデオの記録を停止しません。
> * アプリが写真/ビデオカメラをアクティブに使用している場合、Windows デバイスポータルは写真を撮影したり、ビデオを録画したりすることができます。
> * ライブストリーミング:
>   * HoloLens (第1世代) は、Windows デバイスポータルからのライブストリーミング中に、アプリが写真/ビデオカメラにアクセスできないようにします。
>   * アプリが写真/ビデオカメラをアクティブに使用している場合、HoloLens (第1世代) はライブストリームに失敗します。
>   * HoloLens 2 は、アプリが ExclusiveControl モードで写真/ビデオカメラにアクセスしようとしたときに、ライブストリーミングを自動的に停止します。
>   * HoloLens 2 は、アプリが PV カメラをアクティブに使用している間にライブストリームを開始できます。

### <a name="performance-tracing"></a>パフォーマンストレース

Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png) の Windows デバイスポータルの ![パフォーマンストレース] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [パフォーマンストレース] ページ*

HoloLens から[Windows パフォーマンスレコーダー](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (wpr) のトレースをキャプチャします。
* **使用可能なプロファイル**:ドロップダウンから WPR プロファイルを選択し、**開始** をクリックまたはタップしてトレースを開始します。
* **カスタムプロファイル**:PC から WPR プロファイルを選択するには、 **[参照]** をクリックまたはタップします。 **[Upload and start]** (アップロードして開始) をクリックまたはタップすると、トレースが開始します。

トレースを停止するには、[停止] リンクをクリックします。 トレースファイルのダウンロードが完了するまで、このページをそのままにしておきます。

キャプチャした ETL ファイルは、[Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) で開いて分析に使用できます。

### <a name="processes"></a>プロセス

Microsoft HoloLens の Windows デバイスポータルの [![のプロセス] ページ](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens の Windows デバイスポータルの [プロセス] ページ*

現在実行中のプロセスに関する詳細を表示します。 これには、アプリとシステムの両方のプロセスが含まれます。

### <a name="system-performance"></a>System Performance (システム パフォーマンス)

Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png) の Windows デバイスポータルの ![システムパフォーマンス] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [システムパフォーマンス] ページ*

電力消費、フレーム レート、CPU 負荷など、システムの診断情報のグラフをリアルタイムで表示します。

利用可能なメトリックを次に示します。
* **SoC パワー**:1分間の平均平均システムオンチップ電力使用率
* **システム電源**:1分間の平均システム電力使用率
* **フレームレート**:1秒あたりのフレーム数、不足している1秒あたりの VBlanks、連続した見つからない VBlanks
* **GPU**:GPU エンジンの使用率、使用可能な合計の割合
* **CPU**: 使用可能量の合計に対するパーセント
* **I/O**:読み取りと書き込み
* **ネットワーク**:受信および送信済み
* **メモリ**:合計、使用中、コミット、ページング、非ページ化

### <a name="apps"></a>アプリ

Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png) の Windows デバイスポータルの ![アプリ] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [アプリ] ページ*

HoloLens にインストールされているアプリを管理します。
* **インストールされているアプリ**:アプリを削除して開始します。
* **実行中のアプリ**:現在実行中のアプリの一覧を表示します。
* **アプリのインストール**:コンピューター/ネットワーク上のフォルダーからインストールするアプリパッケージを選択します。
* **依存関係**:インストールするアプリの依存関係を追加します。
* **配置**:選択したアプリと依存関係を HoloLens に展開します。

### <a name="app-crash-dumps"></a>アプリクラッシュダンプ

Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png) の Windows デバイスポータルの ![アプリのクラッシュダンプ] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [アプリクラッシュダンプ] ページ*

このページでは、サイドローディングしたアプリのクラッシュ ダンプを収集できます。 クラッシュダンプを収集する各アプリの [**クラッシュダンプを有効**にする] チェックボックスをオンにします。 後でこのページに戻ると、クラッシュ ダンプが収集されています。 [デバッグ用に Visual Studio で](https://msdn.microsoft.com/library/d5zhxt22.aspx)ダンプファイルを開くことができます。

### <a name="file-explorer"></a>エクスプローラー

Microsoft HoloLens](images/fileexplorer-1000px.png) の Windows デバイスポータルの ![ファイルエクスプローラー] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [ファイルエクスプローラー] ページ*

ファイルエクスプローラーを使用して、ファイルを参照、アップロード、およびダウンロードします。 ドキュメントフォルダー、ピクチャフォルダー、および Visual Studio またはデバイスポータルからデプロイしたアプリのローカルストレージフォルダー内のファイルを操作できます。

### <a name="kiosk-mode"></a>キオスク モード

>[!NOTE]
>キオスクモードは、 [Microsoft HoloLens 商用 Suite](commercial-features.md)でのみ使用できます。

Windows デバイスポータルでキオスクモードを有効にするための最新の手順については、Windows IT Pro センターの[キオスクモードでの HoloLens のセットアップ](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)に関する記事をご覧ください。

### <a name="logging"></a>ログの記録

Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png) の Windows デバイスポータルの ![ログページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [ログ記録] ページ*

HoloLens のリアルタイム Windows イベントトレーシング (ETW) を管理します。

**[プロバイダーの非表示]** をオンにすると、**イベント**の一覧のみが表示されます。
* **登録済みのプロバイダー**:ETW プロバイダーとトレースレベルを選択します。 トレース レベルは次のいずれかの値になります。
   1. 異常終了または終了
   2. 重大なエラー
   3. 警告
   4. エラーではない警告

トレースを開始するには、 **[Enable]** (有効にする) をクリックまたはタップします。 **[Enabled Providers]** (有効なプロバイダー) ドロップダウン リストにプロバイダーが追加されます。
* **カスタムプロバイダー**:カスタム ETW プロバイダーとトレースレベルを選択します。 GUID を使用してプロバイダーを識別します。 GUID にはかっこを含めないでください。
* **有効なプロバイダー**:有効なプロバイダーの一覧を表示します。 ドロップダウンからプロバイダーを選択し、 **[Disable]** (無効にする) をクリックまたはタップしてトレースを停止します。 すべてのトレースを中断するには、 **[Stop All]** (すべて停止) をクリックまたはタップします。
* **プロバイダーの履歴**:現在のセッション中に有効にされた ETW プロバイダーを表示します。 無効になっているプロバイダーをアクティブ化するには、 **[Enable]** (有効にする) をクリックまたはタップします。 履歴をクリアするには、 **[Clear]** (クリア) をクリックまたはタップします。
* **イベント**:選択したプロバイダーからの ETW イベントをテーブル形式で一覧表示します。 この表は、リアルタイムで更新されます。 すべての ETW イベントを表から削除するには、表の下にある **[Clear]** (クリア) ボタンをクリックします。 これによってプロバイダーが無効になることはありません。 **[Save to file]** (ファイルに保存) をクリックすると、現在収集されている ETW イベントをローカルの CSV ファイルにエクスポートできます。
* **フィルター**:ID、キーワード、レベル、プロバイダー名、タスク名、またはテキストで収集された ETW イベントをフィルター処理できます。 複数の条件を組み合わせることができます。
   1. 同じプロパティに適用する条件では、これらの条件のいずれかを満たすことができるイベントが表示されます。
   2. 別のプロパティに適用する条件の場合、イベントはすべての条件を満たしている必要があります

たとえば、条件 *(タスク名に ' Foo ' または ' bar ' が含まれている) と、(テキストには ' error ' または ' warning ' が含まれます)* を指定できます。

### <a name="simulation"></a>シミュレーション

Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png) の Windows デバイスポータルの ![シミュレーションページ<br>
*Microsoft HoloLens の Windows デバイスポータルのシミュレーションページ*

テスト用に入力データを記録して再生できます。
* **キャプチャルーム**:ユーザーの周囲の空間マッピングメッシュを含む、シミュレートされたルームファイルをダウンロードするために使用します。 部屋に名前を付け、 **[Capture]** をクリックして、データを. xef ファイルとして PC に保存します。 このルーム ファイルは、HoloLens エミュレーターに読み込むことができます。
* **記録**:記録するストリームを確認し、記録に名前を指定して、 **[レコード]** をクリックまたはタップして記録を開始します。 HoloLens で操作を実行し、 **[停止]** をクリックしてデータを xef ファイルとして PC に保存します。 このファイルは、HoloLens エミュレーターまたはデバイスで読み込むことができます。
* **再生**:[録音の**アップロード**] をクリックまたはタップして、PC から xef ファイルを選択し、データを HoloLens に送信します。
* **コントロールモード**:ドロップダウンから **[既定]** または **[シミュレーション]** を選択し、 **[設定]** ボタンをクリックまたはタップして HoloLens のモードを選択します。 [Simulation] (シミュレーション) を選ぶと、HoloLens の実際のセンサーは無効になり、アップロードされたシミュレーション データが代わりに使われます。 [Simulation] (シミュレーション) に切り替えると、[Default] (既定) に戻すまで、HoloLens は実際のユーザーに応答しなくなります。

### <a name="networking"></a>ネットワーク

Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png) の Windows デバイスポータルの [ネットワーク] ページ ![<br>
*Microsoft HoloLens の Windows デバイスポータルの [ネットワーク] ページ*

HoloLens で Wi-fi 接続を管理します。
* **WiFi アダプター**:ドロップダウンコントロールを使用して、Wi-fi アダプターとプロファイルを選択します。 **[接続]** をクリックまたはタップして、選択したアダプターを使用します。
* **利用可能なネットワーク**:HoloLens が接続できる Wi-fi ネットワークが一覧表示されます。 **[更新]** をクリックまたはタップして、一覧を更新します。
* **IP 構成**:ネットワーク接続の IP アドレスとその他の詳細が表示されます。

### <a name="virtual-input"></a>Virtual Input (仮想入力)

Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png) の Windows デバイスポータルの ![仮想入力] ページ<br>
*Microsoft HoloLens の Windows デバイスポータルの [仮想入力] ページ*

リモート コンピューターから HoloLens にキーボード入力を送信します。

**[仮想キーボード]** の下にある領域をクリックまたはタップして、HoloLens へのキーストロークの送信を有効にします。 **入力テキスト**テキストボックスに「」と入力し、 **[送信]** をクリックまたはタップして、キーストロークをアクティブなアプリに送信します。

## <a name="device-portal-rest-apis"></a>デバイスポータル REST API

デバイスポータル内のすべての機能は[REST API](device-portal-api-reference.md)の上に構築されており、必要に応じてデータにアクセスし、デバイスをプログラムで制御できます。
