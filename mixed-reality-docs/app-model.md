---
title: アプリ モデル
description: Windows Mixed Reality は、ユニバーサル Windows プラットフォーム、モデルおよび最新の Windows アプリ用の環境によって提供されるアプリ モデルを使用します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ モデル、ライフ サイクル、UWP は、中断、再開、タイル、ビュー、コントラクト
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602997"
---
# <a name="app-model"></a>アプリ モデル

Windows Mixed Reality によって提供されるアプリ モデルを使用して、[ユニバーサル Windows プラットフォーム](https://docs.microsoft.com/windows/uwp/get-started/)(UWP) モデルと最新の Windows アプリ用の環境。 UWP アプリのモデルでは、アプリは、インストールされている、更新、バージョン管理された方法を定義し、安全かつ完全に削除します。 アプリケーションのライフ サイクル - アプリを実行、スリープ状態および終了方法、および状態を保持する方法を制御します。 統合とオペレーティング システム、ファイル、およびその他のアプリとの対話についても説明します。

![2D のアプリ、Windows Mixed Reality ホーム朝食領域内での配置](images/20160112-055908-hololens-500px.jpg)<br>
*Windows Mixed Reality ホームに配置された 2D のビューを使用したアプリ*

## <a name="app-lifecycle"></a>アプリのライフサイクル

Mixed reality アプリのライフ サイクルには、配置、起動、終了、および削除などの標準的なアプリの概念が含まれます。

### <a name="placement-is-launch"></a>Placement が起動

複合現実でアプリのタイルを配置することで、すべてのアプリを開始 (だけ、 [Windows セカンダリ タイル](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) で、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)します。 これらのアプリ タイルの配置、実行が開始されますアプリ。 これらのアプリ タイルを永続化および配置場所の場所を維持するときは必ずのランチャーがアプリに取得するように動作しています。

![配置の世界でのセカンダリ タイルを配置します。](images/slide1-600px.png)<br>
*配置の世界でのセカンダリ タイルを配置します。*

配置が完了するとすぐに (によって、配置が開始された場合を除き、[アプリへ](app-model.md#protocols)起動)、アプリが起動を開始します。 Windows Mixed Reality は、アプリの数に制限を同時に実行できます。 配置して、アプリを起動して、すぐ配置した場所にそのアプリのタイルをアプリの最新の状態のスクリーン ショットのまま他の作業中のアプリが中断可能性があります。 参照してください[Windows 10 UWP アプリのライフ サイクル](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle)resume およびその他のアプリのライフ サイクル イベントの処理の詳細についてはします。

![タイルを配置した後、アプリが実行を開始](images/slide2-500px.png)![実行中、中断または実行されていないアプリの状態ダイアグラム](images/ic576232-500px.png)<br>
*Left: タイルを配置した後、アプリが実行を開始します。実行中、中断、または実行されていないアプリの右: 状態の図。*

### <a name="remove-is-closeterminate-process"></a>削除がプロセスを閉じる/終了

世界中から配置されたアプリのタイルを削除すると、基になるプロセスを閉じます。 アプリが終了したことを確認または問題のあるアプリの再起動のための便利なことができます。

### <a name="app-suspensiontermination"></a>アプリの中断または終了

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)ユーザーがアプリの複数のエントリ ポイントを作成できません。 このように、[スタート] メニューからアプリを起動して、世界中のアプリ タイルを配置することです。 各アプリのタイルは、異なるエントリ ポイントとして動作し、個別のタイルのインスタンスに、システム。 クエリの[SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)なります、 **SecondaryTile**の各アプリ インスタンス。

UWP アプリが中断時に現在の状態のスクリーン ショットが取得されます。

![中断されたアプリのスクリーン ショットを表示します。](images/slide9-800px.png)<br>
*中断されたアプリのスクリーン ショットを表示します。*

他の Windows 10 のシェルから 1 つの重要な違いは、アプリに通知を使用してアプリのインスタンスのアクティブ化の方法は、 [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming)と[CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)イベント。

|  シナリオ |  Resuming  |  アクティブ | 
|----------|----------|----------|
|  [スタート] メニューからアプリの新しいインスタンスを起動します。  |   |  **アクティブ化される**を新しい[TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  [スタート] メニューからのアプリの 2 番目のインスタンスを起動します。  |   |  **アクティブ化される**を新しい**TileId** | 
|  現在アクティブでないアプリのインスタンスを選択します。  |   |  **アクティブ化される**で、 **TileId**インスタンスに関連付けられています。 | 
|  別のアプリを選択し、以前にアクティブなインスタンスを選択します。  |  **再開**発生します  |  | 
|  別のアプリを選択し、以前にアクティブだったインスタンスを選択します。  |  **再開**発生します  |  **Activated**で、 **TileId**インスタンスに関連付けられています。 | 

### <a name="extended-execution"></a>拡張実行

アプリがバック グラウンドでの作業やオーディオの再生を続行する必要があります。 [バック グラウンド タスク](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)HoloLens では使用できます。

![アプリがバック グラウンドで実行できます。](images/slide10-800px.png)<br>
*アプリがバック グラウンドで実行できます。*

## <a name="app-views"></a>アプリ ビュー

アプリがアクティブ化、表示するなど、ビューの種類を選択できます。 アプリの**CoreApplication**、プライマリは常に[アプリ ビュー](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView)とアプリのビューを作成するにはさらに任意の数。 デスクトップでは、ウィンドウとしてアプリのビューの考えることができます。 プライマリ アプリケーション ビューの Unity プロジェクトの作成、複合現実アプリ テンプレート[没入型](app-views.md)します。 

アプリでは、アプリ内購入などの Windows 10 の機能を使用する、XAML などのテクノロジを使用して、追加の 2D アプリ ビューを作成できます。 その他の Windows 10 デバイス用の UWP アプリとしてアプリが開始されている場合は、プライマリ ビューは、2 D がする可能性があります「点灯」複合現実で volumetrically エクスペリエンスを表示する没入型である追加のアプリ ビューを追加することで。 スライド ショー ボタンが世界とサーフェスの間で、アプリから写真を飛行する没入型のアプリ ビューに切り替え、XAML でフォト ビューアー アプリのビルドを想像してください。

![実行中のアプリは、2 D のビューまたは没入型のビューを持つことができます。](images/slide3-800px.png)<br>
*実行中のアプリは、2 D のビューまたは没入型のビューを持つことができます。*

### <a name="creating-an-immersive-view"></a>没入型のビューを作成します。

複合現実アプリはにより実現されます、没入型の表示を作成する、 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace)型。

デスクトップから起動された場合でも、起動時に没入型のビューは純粋に体感型アプリを作成することが常にあります。 没入型のビューは、常に、内から作成された場所に関係なく、ヘッドセット表示します。 没入型のビューをアクティブ化、Mixed Reality ポータルを表示し、ヘッドセットを配置するユーザーをガイドします。

デスクトップ モニターで 2D ビューで始まるアプリには、ヘッドセットでコンテンツを表示する場合は、セカンダリ没入型ビューを作成できます。 この例は、ヘッドセットの 360 度のビデオを表示するモニターの 2D Edge ウィンドウです。

![没入型のビューで実行されているアプリは 1 つの表示のみ](images/slide4-800px.png)<br>
*没入型のビューで実行中のアプリが 1 つの表示のみ*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームで 2D のビュー

没入型のビュー以外は、世界では 2D のビューとしてレンダリングされます。

アプリ、ヘッドセットとデスクトップの両方のモニターで 2D のビューがあります。 新しい 2D ビューが、モニターまたはヘッドセットで、作成したビューとして同じシェル内に配置することに注意してください。 現在では、アプリまたは Mixed Reality ホームとモニターの 2D のビューを移動することはできません。

![2D のビューで実行されているアプリでは、他のアプリと混在の世界で領域を共有します。](images/slide5-800px.png)<br>
*2D のビューで実行されているアプリの他のアプリを使用して領域を共有します。*

### <a name="placement-of-additional-app-tiles"></a>その他のアプリ タイルの配置

使用すると、世界の 2D で多くのアプリを表示を配置することができます、[セカンダリ タイル Api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)します。 これらの「固定」タイルは、ユーザーが配置する必要があり、し、後で使用できるアプリを起動することに、スプラッシュ スクリーンとして表示されます。 Windows Mixed Reality では、2 D タイル コンテンツをライブ タイルとしてレンダリングを現在はサポートしていません。

![アプリは、セカンダリ タイルを使用して複数の配置を持つことができます。](images/slide6-800px.png)<br>
*アプリは、セカンダリ タイルを使用して複数の配置を持つことができます。*

### <a name="switching-views"></a>ビューの切り替え

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>2D の XAML ビューから、没入型のビューへの切り替え

アプリが XAML では、その後、XAML を使用する場合[IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource)アプリの最初のビューを制御します。 アプリをアクティブ化する前に、没入型のビューに切り替える必要があります、 **CoreWindow**没入型エクスペリエンスに直接、アプリが起動するようにしてください。

使用[CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)と[ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_)アクティブなビューを変更します。

> [!NOTE]
>* 指定しない、 [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)フラグを**SwitchAsync**と XAML ビューから、没入型のビュー、またはアプリを起動しスレートへの切り替えは削除されます世界です。
>* **SwitchAsync**を使用して呼び出す必要があります、[ディスパッチャー](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)に切り替えるビューに関連付けられています。
>* 必要があります**SwitchAsync**を仮想キーボードを起動するか、別のアプリをアクティブ化する必要がある場合は、XAML ビューに戻ります。

![アプリは 2D のビューとビューの没入型の間で切り替えることができます](images/slide7-600px.png)![混合の世界と他のアプリが非表示には、アプリは、没入型のビューになったら、](images/slide8-600px.png)<br>
*[左]: アプリは 2D のビューとビューの没入型の間で切り替えることができます。右: 没入型の表示になると、アプリ、Windows Mixed Reality ホームおよびその他のアプリが消えます。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>キーボードの XAML ビューに戻る没入型のビューからの切り替え

ビューの切り替えの前後の 1 つの一般的な理由は、mixed reality アプリで、キーボードに表示されています。 シェルでは、アプリには、2 D のビューが表示されている場合、システムのキーボードを表示するだけです。 を、アプリがテキスト入力を取得する必要がある場合は、テキスト入力フィールドにカスタム XAML ビューを提供に切り替えてし、し、切り替えが完了すると、入力後に、可能性があります。

同様に使用することができます、前のセクションで**ApplicationViewSwitcher.SwitchAsync**没入型のビューから XAML ビューに移行します。

## <a name="app-size"></a>アプリのサイズ

2D アプリ ビューは、固定仮想スレートで常に表示されます。 これにより、すべての 2D ビューがコンテンツの正確な同じ金額を表示します。 アプリの 2D ビューのサイズに関する詳細を次に示します。
* アプリの縦横比がサイズ変更中に保持されます。
* アプリ[解像度とスケール ファクター](building-2d-apps.md#2d-app-view-resolution-and-scale-factor)サイズを変更しては変更されません。
* アプリは、世界中の実際のサイズを照会できません。

![2D アプリケーションは、固定ウィンドウ サイズが表示されます。](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*2D のビューを使用したアプリは固定ウィンドウ サイズで表示されます。*

## <a name="app-tiles"></a>アプリのタイル

[スタート] メニューは標準の小さなタイルと中程度のタイルのピンを使用し、**すべてのアプリ**複合現実での一覧。 

![Windows Mixed Reality [スタート] メニュー](images/start-500px.png)<br>
*Windows Mixed Reality [スタート] メニュー*

## <a name="app-to-app-interactions"></a>アプリの相互作用するアプリ

アプリを作成すると、Windows 10 で使用できる豊富なアプリへの通信メカニズムへのアクセスがあります。 プロトコルの新しい Api やファイルの登録の多くは、HoloLens アプリの起動との通信を有効にするに完璧に動作します。 

デスクトップ ヘッドセットは、指定したファイル拡張子に関連付けられているアプリまたはあるプロトコルの Win32 アプリまたはデスクトップのスレートのデスクトップ モニターでのみ表示される可能性がありますに注意してください。

### <a name="protocols"></a>プロトコル

HoloLens のサポートを使用してアプリにアプリを起動する、 [Windows.System.Launcher Api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)します。

これには別のアプリケーションを起動するときに考慮事項があります。

* 非モーダル起動を実行する場合など、 [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)ユーザーは対話する前に、アプリを配置する必要があります。

* などをモーダルの起動を実行する場合[LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)、モーダルのアプリは、ウィンドウの上に配置されます。

* Windows Mixed Reality は、排他ビュー上でアプリケーションを重ね合わせることはできません。 起動したアプリを表示するには Windows バックアップ アプリケーションを表示する、世界中にユーザーを移動します。

### <a name="file-pickers"></a>ファイル ピッカー

HoloLens は両方ともサポート[FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker)と[FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker)コントラクト。 ただし、アプリにないプレインストールされている、ファイル ピッカー コントラクトと一致します。 これらのアプリ - OneDrive の例では、Microsoft Store からインストールできます。

ピッカーの 1 つ以上のアプリをインストールした場合は表示されませんあいまいさを排除 UI を起動します。 どのアプリを選択するため代わりに、インストールされている最初のファイル ピッカーが選択されます。 ファイルを保存するときに、タイムスタンプを含むファイル名が生成されます。 これは、ユーザーによって変更ことはできません。

既定では、次の拡張機能はローカルでサポートされます。

|  App  |  拡張機能 | 
|----------|----------|
|  フォト  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>アプリ コントラクトと Windows Mixed Reality 拡張機能

アプリ コントラクトと拡張ポイントを使用すると、ファイル拡張子を処理またはバック グラウンド タスクを使用するように、オペレーティング システムのより深い機能を活用するためにアプリを登録できます。 これは、サポートされているとサポート非対象のコントラクトと HoloLens の拡張ポイントの一覧です。

|  コントラクトまたは拡張機能  |  サポートされていますか。 | 
|----------|----------|
| [アカウントの画像プロバイダー (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | サポートされません | 
| [アラーム](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | サポートされません | 
| [アプリ サービス](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | サポートされているが完全に機能していません。 | 
| [予定プロバイダー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | サポートされません | 
| [自動再生 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | サポートされません | 
| [バック グラウンド タスク (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | (すべてのトリガー作業) を部分的にサポート | 
| [更新タスク (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | サポートされている | 
| [キャッシュ ファイル更新ツール コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | サポートされている | 
| [カメラ設定 (拡張)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | サポートされません | 
| [ダイヤル プロトコル](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | サポートされません | 
| [ファイルのアクティブ化 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | サポートされている | 
| [ファイル オープン ピッカー コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | サポートされている | 
| [ファイル保存ピッカー コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | サポートされている | 
| [ロック画面の呼び出し](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | サポートされません | 
| [メディア再生](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | サポートされません | 
| [リモート再生コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | サポートされません | 
| [プレインストールされている構成タスク](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | サポートされません | 
| [プリント 3D ワークフロー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | サポートされている | 
| [印刷タスク設定 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | サポートされません | 
| [URI のアクティブ化 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | サポートされている | 
| [制限された起動](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | サポートされません | 
| [検索コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | サポートされません | 
| [設定コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | サポートされません | 
| [共有コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | サポートされません | 
| [(拡張子) を SSL 証明書.](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | サポートされている | 
| [Web アカウント プロバイダー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | サポートされている | 

## <a name="app-file-storage"></a>アプリのファイル ストレージ

すべての記憶域は、 [Windows.Storage 名前空間](https://docs.microsoft.com/uwp/api/Windows.Storage)します。 詳細については、次のドキュメントを参照してください。 HoloLens では、アプリケーション ストレージ同期/ローミングすることはできません。

* [ファイル、フォルダー、およびライブラリ](https://docs.microsoft.com/windows/uwp/files/index)
* [設定と他のアプリ データを保存して取得する](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>既知のフォルダー

参照してください[KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders)の UWP アプリの完全な詳細情報。

<table>
<tr>
<th> プロパティ</th><th> HoloLens でサポートされています</th><th> イマーシブ ヘッドセットでサポートされています</th><th> 説明</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>アプリはフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>カメラ ロール フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>ドキュメント ライブラリを取得します。 ドキュメント ライブラリは、一般的な使用するためのものではありません。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>音楽ライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>オブジェクト 3D フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>画像ライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">再生リスト</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>再生リスト フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>画像の保存フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>ビデオ ライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">ホーム グループ</a></td><td></td><td style="text-align: center;">✔️</td><td>ホーム グループ フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>サーバー (Digital Living Network Alliance (DLNA)) デバイスのメディアのフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>録音された通話フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>リムーバブル デバイス フォルダーを取得します。</td>
</tr>
</table>

## <a name="app-package"></a>アプリ パッケージ

Windows 10 では不要になった対象オペレーティング システムが代わりに[アプリの対象に 1 つまたは複数のデバイス ファミリ](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)します。 デバイス ファミリに基づいて、デバイス ファミリのデバイス全体で想定できる API、システム特性、動作を特定します。 一連のデバイスにアプリをインストールしてからも決定、 [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)します。

* ヘッドセットのデスクトップ、HoloLens の両方を対象とするアプリの対象に、 **Windows.Universal**デバイス ファミリ。
* デスクトップだけヘッドセットを対象とするアプリの対象、 **Windows.Desktop**デバイス ファミリ。
* HoloLens だけを対象とするアプリの対象、 **Windows.Holographic**デバイス ファミリ。

## <a name="see-also"></a>関連項目

* [アプリのビュー](app-views.md)
* [複合現実の 2D の UWP アプリを更新します。](building-2d-apps.md)
* [3D アプリ起動ツールの設計ガイダンス](3d-app-launcher-design-guidance.md)
* [3D アプリ ランチャーを実装します。](implementing-3d-app-launchers.md)
