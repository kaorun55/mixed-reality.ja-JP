---
title: Windows Device Portal のを使用
description: HoloLens の Windows Device Portal では、構成して、Wi-fi または USB 経由でデバイスをリモートで管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイスのポータルには、HoloLens とデバッグを管理し、アプリを最適化するのに役立つ多くのツールが含まれています。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal、HoloLens
ms.openlocfilehash: 8b9935d6b64abfd22e2e856e0142c953a6366008
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600964"
---
# <a name="using-the-windows-device-portal"></a>Windows Device Portal のを使用

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens の Windows Device Portal では、構成して、Wi-fi または USB 経由でデバイスをリモートで管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイスのポータルには、HoloLens とデバッグを管理し、アプリを最適化するのに役立つ多くのツールが含まれています。

このドキュメントは、HoloLens の Windows Device Portal について具体的には。 デスクトップ (Windows Mixed Reality を含む) の Windows デバイスのポータルを使用する、次を参照してください[Windows Device Portal の概要。](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Windows Device Portal を使用する、HoloLens の設定

1. HoloLens の電源を入れ、デバイスを装着します。
2. [ブルーム](gestures.md#bloom) ジェスチャを実行して、メイン メニューを開きます。
3. 見つめます、**設定**タイルし、実行、[エア タップ](gestures.md#air-tap)ジェスチャ。 環境内でアプリを配置する 2 つ目エア タップを実行します。 配置すると、設定アプリが起動します。
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[Developer Mode]** (開発者モード) を有効にします。
7. [下へスクロール](gestures.md#composite-gestures)を有効にして**デバイス ポータル**します。
8. Windows Device Portal を設定するため、この HoloLens にアプリを展開するには USB または Wifi 経由で、クリックして**ペア**に[ペアリング PIN を生成](using-visual-studio.md#pairing-your-device-hololens)します。 Visual Studio に最初の展開時に PIN を入力するまでは、設定アプリ PIN ポップアップのままにします。

   ![Windows Holographic の設定 アプリの開発者モードを有効にします。](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Wi-fi 経由で接続します。

1. [Wi-fi に接続する、HoloLens](connecting-to-wi-fi-on-hololens.md)します。
2. デバイスの IP アドレスを検索します。
   * デバイスの IP アドレスを調べる**設定 > ネットワークとインターネット > Wi-fi > 高度なオプション**します。
3. お使いの PC 上の web ブラウザーから https://<YOUR_HOLOLENS_IP_ADDRESS> に移動します。
   * ブラウザー、次のメッセージが表示されます。「この web サイトのセキュリティ証明書に問題があるです」 これは、Device Portal に発行された証明書がテスト証明書であるためです。 ここでは、この証明書エラーを無視して続行できます。

## <a name="connecting-over-usb"></a>USB 経由で接続します。

1. [ツールをインストールする](install-the-tools.md)お使いの PC にインストールされている Windows 10 開発者ツールの Visual Studio Update 1 があるかどうかを確認します。 これで USB 接続が有効になります。
2. マイクロ USB ケーブルを使って HoloLens を PC に接続します。
3. PC 上の Web ブラウザーから、 http://127.0.0.1:10080 にアクセスします。

## <a name="connecting-to-an-emulator"></a>エミュレーターに接続します。

Device Portal はエミュレーターで使うこともできます。 デバイスのポータルに接続するには、使用、[ツールバー](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)します。 次のアイコンをクリックします。![デバイスのポータルを開く アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。

## <a name="creating-a-username-and-password"></a>ユーザー名とパスワードを作成します。

![Windows Device Portal へのアクセスを設定します。](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows Device Portal へのアクセスを設定します。*

HoloLens で初めて Device Portal に接続するときは、ユーザー名とパスワードを作成する必要があります。
1. PC 上の Web ブラウザーで、HoloLens の IP アドレスを入力します。 [Set up access] (アクセスのセットアップ) ページが開きます。
2. クリックしてまたはタップします**要求 pin**し、生成された PIN を取得する HoloLens の表示を確認します。
3. PIN の入力、**デバイスで表示された PIN**テキスト ボックス。
4. Device Portal への接続に使うユーザー名を入力します。 Microsoft アカウント (MSA) 名やドメイン アカウント名を指定する必要はありません。
5. パスワードを入力し、確認用にもう一度入力します。 パスワードは 7 文字以上にする必要があります。 MSA やドメインのパスワードと同じにする必要はありません。
6. クリックして**ペア**HoloLens で Windows Device Portal に接続します。

をいつでもでも、このユーザー名またはパスワードを変更する場合、このプロセスを繰り返しクリックするか、デバイスのセキュリティ ページを参照してください、**セキュリティ**上部右、またはに移動するリンク: https://<YOUR_HOLOLENS_IP_アドレス >/devicesecurity.htm します。

## <a name="security-certificate"></a>セキュリティ証明書

ブラウザーで "証明書エラー" が表示される場合は、デバイスとの信頼関係を作成することで修正できます。

ぞれぞれの HoloLens では、SSL 接続用に一意の自己署名証明書が生成されます。 既定では、この証明書が PC の Web ブラウザーによって信頼されていないため、"証明書エラー" が発生することがあります。 この証明書を HoloLens から (USB または信頼している Wi-Fi ネットワーク経由で) ダウンロードし、PC で信頼すると、デバイスに安全に接続できます。
1. **(USB または信頼できる、Wi-fi ネットワーク) のセキュリティで保護されたネットワーク上にいることを確認します。**
2. このデバイスの証明書は、デバイス ポータルの [セキュリティ] ページからダウンロードします。
   * クリックするか、**セキュリティ**アイコンの右上のリストからのリンクをまたはに移動します https://<YOUR_HOLOLENS_IP_ADDRESS>/devicesecurity.htm。
3. お使いの PC でのストアの「信頼されたルート証明機関」証明書をインストールします。
   * Windows メニューでは、次のように入力します。コンピューターの証明書を管理し、アプレットを開始します。
   * 展開、**信頼されたルート証明機関**フォルダー。
   * をクリックして、**証明書**フォルダー。
   * [操作] メニューから選択します。すべてのタスク > インポートしています.
   * Device Portal からダウンロードした証明書ファイルを使って、証明書のインポート ウィザードを完了します。
4. ブラウザーを再起動します。

## <a name="device-portal-pages"></a>Device Portal のページ

### <a name="home"></a>Home

![Microsoft HoloLens の Windows Device Portal のホーム ページ](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens の Windows Device Portal のホーム ページ*

Device Portal セッションは Home (ホーム) ページから始まります。 他のページにアクセスするには、ホーム ページの左側にあるナビゲーション バーを使います。

ページの最上部にあるツール バーでは、よく使われる状態や機能にアクセスできます。
* **オンライン**:デバイスが Wi-fi に接続されているかどうかを示します。
* **シャット ダウン**:デバイスをオフにします。
* **再起動**:デバイスの電源が循環します。
* **セキュリティ**:デバイスのセキュリティ ページが開きます。
* **クール**:デバイスの温度を示します。
* **A/C**:デバイスが接続されているかどうかを示し、充電中です。
* **ヘルプ**:REST インターフェイスのドキュメント ページが開きます。

ホーム ページには次の情報が表示されます。
* **デバイスの状態:** デバイスの正常性を監視し、重大なエラーを報告します。
* **Windows 情報:** HoloLens の名前と現在インストールされている Windows のバージョンを示しています。
* **[Preferences]** (設定) セクションには次の設定が含まれます。
   * **IPD**:ミリメートル単位のまっすぐに検索するときに、ユーザーの瞳孔 center との間での距離である interpupillary 距離 (IPD) を設定します。 設定はすぐに反映されます。 既定値は、デバイスのセットアップ時に自動的に計算された値です。
   * **デバイス名**:名前、HoloLens を指定します。 この値を変更した場合、変更を有効にするにはデバイスを再起動する必要があります。 クリックすると**保存**、ダイアログ ボックスは、デバイスをすぐに再起動するか、後で再起動するかどうかを確認します。
   * **スリープの設定**:バッテリで実行されると、デバイスがスリープ モード接続されていることになる前に待機する時間の長さを設定します。

### <a name="3d-view"></a>3D View (3D ビュー)

![Microsoft HoloLens で Windows Device Portal での 3D の表示 ページ](images/3dview-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal での 3D の表示 ページ*

[3D View] (3D ビュー) ページを使うと、HoloLens がどのように周囲を解釈するかを確認できます。 ビュー内を移動するには、マウスを次のように使います。
* 左クリックして + マウス; 回転。
* パン: 右マウスを押しながらクリック
* ズーム: マウスのスクロールします。
* **追跡オプション**
   * チェックして継続的なビジュアルの追跡を有効に**Force visual 追跡**します。 
   * **一時停止**visual 追跡を停止します。
* **ビューのオプションを**:3D 表示のオプションを設定します。
  * **追跡**:ビジュアルの追跡が有効かどうかを示します。
  * **フロアを表示する**:格子模様の床面を表示します。
  * **表示の視錐台**:視錐台が表示されます。
  * **安定化平面表示**:HoloLens がモーションを安定化に使用する面を表示します。
  * **メッシュを表示する**:環境を表す空間マッピング メッシュが表示されます。
  * **空間のアンカーを表示**:作業中のアプリに対する空間アンカーを表示します。 取得やアンカーの更新の更新ボタンをクリックする必要があります。
  * **詳細の表示**:表示は、リアルタイムで変更するときの位置、ヘッドの回転の四元数、およびデバイスの配信元のベクターを渡します。
  * **全画面表示ボタン**:全画面表示モードで、3 D 表示を示しています。 Esc キーを押すと全画面表示を終了します。
* **再構築のサーフェス**:をクリックしてまたはタップします**Update**空間マッピング最新メッシュ デバイスからを表示します。 全体の処理が完了するまでには、最大で数秒かかる可能性があります。 3D のビューで、メッシュが自動的に更新されないと、手動でクリックする必要があります**更新**デバイスから最新のメッシュを取得します。 クリックして**保存**空間マッピングの現在のメッシュを PC 上で、obj ファイルとして保存します。
* **空間アンカー**:表示または更新中のアプリに対する空間アンカーする更新プログラムをクリックします。

### <a name="mixed-reality-capture"></a>Mixed Reality キャプチャ

![Microsoft HoloLens で Windows Device Portal での混合の実際のキャプチャ ページ](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal での混合の実際のキャプチャ ページ*

使用して、 [Mixed Reality キャプチャ](mixed-reality-capture.md)HoloLens のメディア ストリームを保存するページ。
* **設定**:次の設定を確認して記録されたメディア ストリームを制御します。
  * **ホログラム**:ビデオ ストリームの holographic のコンテンツをキャプチャします。 ホログラムは、ステレオではなくモノラルでレンダリングされます。
  * **PV カメラ**:写真/ビデオ カメラからビデオ ストリームをキャプチャします。
  * **マイクのオーディオ**:アレイ マイクからオーディオをキャプチャします。
  * **アプリの音声**:現在実行中のアプリからのオーディオをキャプチャします。
  * **ライブ プレビュー品質**:画面の解像度、フレーム レート、およびストリーミング レートのライブ プレビューを選択します。
* をクリックしてまたはタップします、**ライブ プレビュー**キャプチャ ストリームを表示するボタンをクリックします。 **ライブ プレビューを停止**キャプチャ ストリームを停止します。
* をクリックしてまたはタップします**レコード**複合現実のストリームを記録する、指定した設定を使用して開始します。 **記録を停止**録音を終了し、保存します。
* をクリックしてまたはタップします**Take photo**キャプチャ ストリームから静止画像を取得します。
* **ビデオや写真**:デバイスで作成されたビデオや写真のキャプチャの一覧が表示されます。

Device Portal からライブ プレビューを記録またはストリーミングしている間、HoloLens アプリでは MRC の写真やビデオをキャプチャできないことに注意してください。

### <a name="performance-tracing"></a>パフォーマンス トレース

![Microsoft HoloLens で Windows Device Portal 内のページのトレースのパフォーマンス](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal 内のページのトレースのパフォーマンス*

キャプチャ[Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) HoloLens から (WPR) のトレース。
* **使用可能なプロファイル**:ドロップダウン リスト、およびクリックまたはタップしますから WPR プロファイルを選択**開始**トレースを開始します。
* **カスタム プロファイル**:をクリックしてまたはタップします**参照**を PC から WPR プロファイルを選択します。 **[Upload and start]** (アップロードして開始) をクリックまたはタップすると、トレースが開始します。

トレースを停止するには、停止リンクをクリックします。 トレース ファイルのダウンロードが完了するまで、このページに留まります。

キャプチャした ETL ファイルは、[Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) で開いて分析に使用できます。

### <a name="processes"></a>Processes (プロセス)

![Microsoft HoloLens で Windows Device Portal で [プロセス] ページ](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal で [プロセス] ページ*

現在実行中のプロセスに関する詳細を表示します。 これには、アプリとシステムの両方のプロセスが含まれます。

### <a name="system-performance"></a>System Performance (システム パフォーマンス)

![Microsoft HoloLens で Windows Device Portal でのシステム パフォーマンス ページ](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのシステム パフォーマンス ページ*

電力消費、フレーム レート、CPU 負荷など、システムの診断情報のグラフをリアルタイムで表示します。

利用可能なメトリックを次に示します。
* **SoC power**:瞬間的なシステムを搭載の電源の使用率、1 つ分の間での平均
* **システム電源**:瞬間的なシステム電源の使用率、1 つ分の間での平均
* **フレーム レート**:1 秒あたりのフレームには、1 秒あたりの VBlanks および連続して本件 VBlanks が実行されなかった場合
* **GPU**:GPU エンジンの使用率、使用可能な合計の割合
* **CPU**: 使用可能量の合計に対するパーセント
* **I/O**:読み取りと書き込み
* **ネットワーク**:受信し、送信
* **メモリ**:コミットされ、使用中の合計がページ、および非ページ

### <a name="apps"></a>アプリ

![Microsoft HoloLens で Windows Device Portal でのアプリ ページ](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのアプリ ページ*

HoloLens にインストールされているアプリを管理します。
* **アプリがインストールされている**:削除し、アプリを起動します。
* **アプリを実行している**:現在実行されているアプリの一覧を表示します。
* **アプリをインストール**:コンピューターまたはネットワーク上のフォルダーからインストール用のアプリ パッケージを選択します。
* **依存関係**:インストールしようとするアプリの依存関係を追加します。
* **デプロイ**:選択したアプリとの依存関係を HoloLens にデプロイします。

### <a name="app-crash-dumps"></a>アプリのクラッシュ ダンプ

![Microsoft HoloLens で Windows Device Portal でアプリのクラッシュ ダンプのページ](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でアプリのクラッシュ ダンプのページ*

このページでは、サイドローディングしたアプリのクラッシュ ダンプを収集できます。 チェック、**クラッシュ ダンプを有効になっている**クラッシュ ダンプを収集する各アプリのチェック ボックスをオンします。 後でこのページに戻ると、クラッシュ ダンプが収集されています。 ファイルをダンプできます[デバッグ用の Visual Studio で開かれている](https://msdn.microsoft.com/library/d5zhxt22.aspx)します。

### <a name="file-explorer"></a>エクスプローラー

![Microsoft HoloLens で Windows Device Portal でのファイル エクスプ ローラー ページ](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのファイル エクスプ ローラー ページ*

[参照]、アップロード、およびファイルをダウンロードするには、ファイル エクスプ ローラーを使用します。 Visual Studio またはデバイスのポータルからデプロイされたアプリの Documents フォルダー、ピクチャ フォルダーに、ローカル ストレージ フォルダーのファイルを使用することができます。

### <a name="kiosk-mode"></a>キオスク モード

>[!NOTE]
>キオスク モードはのみ使用できます、 [Microsoft HoloLens Commercial Suite](commercial-features.md)します。

確認してください、[キオスク モードを設定する HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) Windows IT Pro Center Windows Device Portal でのキオスク モードを有効にする手順については最新の記事。

### <a name="logging"></a>ログの記録

![Microsoft HoloLens で Windows Device Portal でのログ記録 ページ](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのログ記録 ページ*

Event Tracing for Windows (ETW)、HoloLens でリアルタイムに管理します。

確認**プロバイダーを非表示に**を表示する、**イベント**のみを一覧表示します。
* **登録済みプロバイダー**:ETW プロバイダーと、トレース レベルを選択します。 トレース レベルは次のいずれかの値になります。
   1. 異常終了または終了
   2. 重大なエラー
   3. 警告
   4. エラーではない警告

トレースを開始するには、**[Enable]** (有効にする) をクリックまたはタップします。 **[Enabled Providers]** (有効なプロバイダー) ドロップダウン リストにプロバイダーが追加されます。
* **カスタム プロバイダー**:カスタムの ETW プロバイダーと、トレース レベルを選択します。 GUID を使用してプロバイダーを識別します。 GUID にはかっこを含めないでください。
* **プロバイダーを有効になっている**:有効なプロバイダーを一覧表示します。 ドロップダウンからプロバイダーを選択し、**[Disable]** (無効にする) をクリックまたはタップしてトレースを停止します。 すべてのトレースを中断するには、**[Stop All]** (すべて停止) をクリックまたはタップします。
* **プロバイダーの履歴**:現在のセッション中に有効にしていた ETW プロバイダーを示しています。 無効になっているプロバイダーをアクティブ化するには、**[Enable]** (有効にする) をクリックまたはタップします。 履歴をクリアするには、**[Clear]** (クリア) をクリックまたはタップします。
* **イベント**:表形式で選択したプロバイダーから ETW イベントを一覧表示します。 この表は、リアルタイムで更新されます。 、テーブルの下には、をクリックして、**クリア**テーブルからすべての ETW イベントを削除するボタンをクリックします。 これによってプロバイダーが無効になることはありません。 **[Save to file]** (ファイルに保存) をクリックすると、現在収集されている ETW イベントをローカルの CSV ファイルにエクスポートできます。
* **フィルター**:ID、キーワード、レベル、プロバイダーの名前、タスクの名前、またはテキストによって収集された ETW イベントをフィルター処理できます。 いくつかの条件を組み合わせることができます。
   1. 適用する条件のこれらの条件のいずれかを示す、同じプロパティでイベントを満たすことができます。
   2. 条件のさまざまなプロパティに適用する、イベントは、すべての条件を満たす必要があります

たとえば、条件を指定できます *(タスク名には、'Foo' または 'バー' が含まれています)、(テキストには、'error' または '警告' が含まれています)*

### <a name="simulation"></a>シミュレーション

![Microsoft HoloLens で Windows Device Portal でのシミュレーションのページ](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのシミュレーションのページ*

テスト用に入力データを記録して再生できます。
* **ルームのキャプチャ**:ユーザーの環境の空間マッピングのメッシュを含むシミュレートされた部屋ファイルをダウンロードするために使用します。 ルームの名前を指定し、をクリックし、**キャプチャ**PC 上の .xef ファイルとしてデータを保存します。 このルーム ファイルは、HoloLens エミュレーターに読み込むことができます。
* **記録**:録音、記録、という名前のストリームを確認し、をクリックしてまたはタップします**レコード**再コーディングを開始します。 クリックして、HoloLens で操作を実行**停止**PC 上の .xef ファイルとしてデータを保存します。 このファイルは、HoloLens エミュレーターまたはデバイスで読み込むことができます。
* **再生**:をクリックしてまたはタップします**アップロード記録**を PC から xef ファイルを選択し、HoloLens にデータを送信します。
* **コントロール モード**:選択**既定**または**シミュレーション**ドロップダウンと をクリックまたはタップしてから、**設定**HoloLens のモードを選択するボタン。 [Simulation] (シミュレーション) を選ぶと、HoloLens の実際のセンサーは無効になり、アップロードされたシミュレーション データが代わりに使われます。 [Simulation] (シミュレーション) に切り替えると、[Default] (既定) に戻すまで、HoloLens は実際のユーザーに応答しなくなります。

### <a name="networking"></a>ネットワーク

![Microsoft HoloLens で Windows Device Portal でのネットワーク ページ](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal でのネットワーク ページ*

HoloLens、Wi-fi 接続を管理します。
* **WiFi アダプター**:ドロップダウン コントロールを使用して Wi-fi アダプターとプロファイルを選択します。 をクリックしてまたはタップします**Connect**選択したアダプターを使用します。
* **使用可能なネットワーク**:Wi-fi ネットワークに接続できる、HoloLens を一覧表示します。 をクリックしてまたはタップします**更新**一覧を更新します。
* **IP 構成**:IP アドレスとその他のネットワーク接続の詳細を示します。

### <a name="virtual-input"></a>Virtual Input (仮想入力)

![Microsoft HoloLens で Windows Device Portal で仮想の入力 ページ](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens で Windows Device Portal で仮想の入力 ページ*

リモート コンピューターから HoloLens にキーボード入力を送信します。

クリックしてまたはタップでリージョン**仮想キーボード**HoloLens を送信するキーストロークを有効にします。 入力、**入力テキスト**テキスト ボックスをクリックしてまたはタップ**送信**キーストロークを作業中のアプリに送信するためです。

## <a name="device-portal-rest-apis"></a>デバイス ポータルの REST API

上に構築、デバイス ポータル内のすべてが[REST API の](device-portal-api-reference.md)データにアクセスし、デバイスの管理をプログラム的にも使用できます。
