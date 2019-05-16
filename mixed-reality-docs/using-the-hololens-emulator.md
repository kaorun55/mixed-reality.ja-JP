---
title: HoloLens のエミュレーターを使用します。
description: HoloLens のエミュレーターを使用して、物理 HoloLens なし、PC 上の複合現実アプリをテストできます。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens、エミュレーター
ms.openlocfilehash: 0dfca73e6c8e1809e1bea3df6ca344b3de0698d5
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730916"
---
# <a name="using-the-hololens-emulator"></a>HoloLens のエミュレーターを使用します。

HoloLens のエミュレーターは、HoloLens の開発ツールセットが付属して物理 HoloLens なし、PC で holographic のアプリをテストすることができます。 エミュレーターでは、HYPER-V 仮想マシンを使用します。 通常、HoloLens のセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。 アプリでは、エミュレーターで実行するように変更する必要はありませんを実際の HoloLens で実行されていないことがわからない。

デスクトップ Pc の Windows Mixed Reality 没入型 (VR) ヘッドセット アプリやゲームを開発する場合、チェック アウト、 [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)、代わりにデスクトップ ヘッドセットをシミュレートすることができます。


## <a name="installing-the-hololens-emulator"></a>HoloLens のエミュレーターをインストールします。
HoloLens のエミュレーターおよび holographic プロジェクト テンプレートをダウンロードします。

バージョン: 
* [HoloLens 2 エミュレーターおよび holographic プロジェクト テンプレート](https://go.microsoft.com/fwlink/?linkid=2087187)します。
* [HoloLens のエミュレーター (第 1 世代) および holographic プロジェクト テンプレート](https://go.microsoft.com/fwlink/?linkid=2065980)します。

HoloLens のエミュレーターの以前のビルドのについて、 [HoloLens のエミュレーターのアーカイブ](hololens-emulator-archive.md)ページ。

### <a name="hololens-emulator-system-requirements"></a>HoloLens のエミュレーターのシステム要件

HoloLens のエミュレーター RemoteFx で HYPER-V を使用する (1 日の汎用エミュレーター) または GPU PV (HoloLens 2 エミュレーター) ハードウェアのグラフィックスを加速します。 エミュレーターを使用するには、PC は、これらのハードウェア要件を満たしていることを確認します。
* 64 ビットの Windows 10 Pro、Enterprise、または教育 
    >[!NOTE]
    >Windows 10 Home エディションは、HYPER-V または HoloLens のエミュレーターをサポートしていません。  
    >HoloLens 2 エミュレーター、Windows 10 年 2018年 10 月の更新を必要がありますまたはそれ以降。
* 64 ビット CPU
* CPU と 4 コア (または複数の Cpu と 4 コアの合計)
* 8 GB 以上の RAM
* 次の機能がある必要があります、BIOS で[サポートされていて有効](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * ハードウェア支援による仮想化
   * Second Level Address Translation (SLAT)
   * ハードウェアベースのデータ実行防止 (DEP)
* GPU の要件
   * DirectX 11.0 以降
   * WDDM 1.2 グラフィックス ドライバーまたは以降 (第 1 世代)
   * WDDM 2.5 グラフィックス ドライバー (HoloLens 2 エミュレーター)
   * エミュレーターでサポートされていない GPU では、機能しますが、大幅に遅くなります

システムが、上記の要件を満たす場合**システムに"HYPER-V"機能が有効になっているか確認してください** コントロール パネル-> プログラム の プログラムと機能の Windows 機能の有効化-> または-> オフことを確認"ハイパー-V"が正常にエミュレーターのインストールの選択されています。

## <a name="deploying-apps-to-the-hololens-emulator"></a>HoloLens のエミュレーターにアプリを展開します。

1. Visual Studio でアプリ ソリューションを読み込みます。
    >[!NOTE]
    >Unity を使用する場合は、Unity からプロジェクトをビルドし、通常どおり Visual Studio に、作成されたソリューションを読み込みます。
2. HoloLens のエミュレーターの (第 1 世代)、プラットフォームに設定されていることを確認**x86**します。 HoloLens 2 エミュレーターいることを確認、プラットフォームに設定されている**x86**または**x64**します。
3. 目的の**HoloLens のエミュレーター**デバッグのターゲット デバイスとしてのバージョン。
4. 移動して**デバッグ > [デバッグ開始]** またはキーを押します**F5**エミュレーターを起動してデバッグ用のアプリをデプロイします。

エミュレーターは、最初に起動するときに起動する、1 分以上かかる場合があります。 開いたままにしておく、エミュレーター、デバッグ セッション中に実行中のエミュレーターにアプリをすばやくデプロイできるようにすることをお勧めします。

## <a name="basic-emulator-input"></a>基本的なエミュレーターの入力

エミュレーターの制御は、多くの一般的な 3 D ビデオ ゲームによく似ています。 入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。 エミュレーターを制御するには、ソックスを着けずに、HoloLens のシミュレートされたユーザーの操作をリダイレクトします。 周囲のシミュレートされたユーザーと、エミュレーターで実行されているアプリが実際のデバイスでこれらと同じように応答するアクションに移動します。

HoloLens の上にカーソル (第 1 世代) は、ヘッドの移動と回転に従います。  HoloLens 2 エミュレーターでは、カーソルは、手の動きと印刷の向きに従います。

* **転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。
* **検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。
* **エア タップ ジェスチャ**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。
* **「Bloom/システム ジェスチャ**- には、キーボード Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。
* **スクロールの移動を渡す**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。
* **移動と印刷の向きを渡す**(HoloLens 2 エミュレーターのみ) - Alt キーを押しながらを/下矢/左/右に移動して手のアイコンにマウスをドラッグするか、方向キーと Q を使用して/E 回転し、して手のアイコンの傾きをします。  Xbox コント ローラーでは、左または右バンパー キーを押しながら右スティック、左/右/前方/戻る、して手のアイコンを移動する左のサムスティックを使用して、回転、およびアップ/ダウンして手のアイコンを上げたり下げたりする Dpad にします。

## <a name="anatomy-of-the-hololens-2-emulator"></a>2 HoloLens のエミュレーターの構造 

### <a name="main-window"></a>メイン ウィンドウ

![HoloLens 2 エミュレーターのメイン ウィンドウ](images/emulator2-900px.png)

### <a name="toolbar"></a>ツール バー

メイン ウィンドウの右側には、エミュレーター ツールバーが表示されます。 ツールバーには、次のボタンが含まれています。
* ![ある閉じるアイコン](images/emulator-close.png)**閉じる**:エミュレーターを閉じます。
* ![最小化アイコン](images/emulator-minimize.png)**最小化**:エミュレーターのウィンドウを最小化します。
* ![Simulation_icon](images/emulator-simulation-panel.png) **シミュレーション コントロール パネルの **:表示または非表示、[シミュレーションのコントロール パネルの ](#simulation-control-panel)の構成と制御の[エミュレーターへの入力](#basic-emulator-input)します。
* ![画面のアイコンに合わせる](images/emulator-fit.png)**画面に合わせる**:エミュレーターの画面に収まるようにします。
* ![[ズーム] アイコン](images/emulator-zoom.png)**ズーム**:大きくしたり小さく、エミュレーターを作成します。
* ![ヘルプ アイコン](images/emulator-help.png)**ヘルプ**:エミュレーターのヘルプを開きます。
* ![開いているデバイスのポータル アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。
* ![ツール アイコン](images/emulator-tools.png)**ツール**:開く、**追加ツール**ウィンドウ。

### <a name="simulation-control-panel"></a>コントロール パネルのシミュレーション

シミュレーションのコントロール パネルを使用して、現在の位置とシミュレートされた人とシミュレートされた入力デバイスの向きを表示できます。  また、手、および PC のキーボード、マウス、ゲームパッドなどのシミュレートされた入力を制御するために使用されるデバイスの一方または両方を非表示など、両方のシミュレートされた入力を構成することもできます。

![コントロール パネルのシミュレーション](images/emulator-simulation-control-panel.png)

* シミュレーション パネルを表示または非表示をツール バー ボタンをクリックします。 または、キーボードの F7 キーを押します。
* コントロールまたは、キーボード、マウス、ゲームパッドのコントロールが含まれており、ツールヒントを表示するフィールドの上にマウスを移動します。
* または、手の形を非表示には、左側または右側にある適切なスイッチを切り替えます。
* 手のアイコンを制御するには、キーボード、ゲームパッドの左側または右側バンパーに、左右の alt キーを使用します。
* 1 つまたは両方の手にすべての入力を指示するには、トグル スイッチで画鋲のアイコンのボタンをクリックします。  これは、手の Alt キーを保持しているのと同じです。
* 目の視線方向を制御するには、「の目」セクションで、プッシュピンをクリックしてします。  これは、キーボードの 'Y' キーを保持しているのと同じです。
* 記録ルームを読み込めません「記録」セクションでは、「ロード」ボタンをクリックします。  参照してください[ルームをシミュレートした](#simulated-rooms)詳細についてはします。
* シミュレートされた人間またはシミュレートされた入力デバイスが移動またはキーボードへの応答を回転する速度を調整するには、マウスまたはゲームパッド入力、[入力の設定] の横にある歯車アイコンをクリックしておよびスライダーを調整します。
* 既定では、キーボード入力は、シミュレートされた人とシミュレートされた入力を制御します。  経由で送信する、HoloLens、PC のキーボード入力がある、「シミュレーションを使用してキーボード。」をオフにします。  F4 キーは、この設定のショートカット キーです。
* シミュレーション パネルが既に表示されている場合、F8 キーを押すと、キーボード フォーカスがそれに移動されます。
* エミュレーター ウィンドウからシミュレーション パネルのドッキングを解除するには、パネルの下部にあるボタンをクリックします。 または、キーボードの F9 キーを押します。  ウィンドウを閉じるか、f9 キーをもう一度押すとは、エミュレーターにウィンドウを返します。
* 接続し、%programfiles(x86) から PerceptionSimulationInput.exe を実行して、HoloLens 2 エミュレーター、HoloLens 2 デバイス、または Windows Mixed Reality シミュレーションを制御することができます、別のアプリケーションとして起動できるシミュレーションのコントロール パネル \Windows Kits\10\Microsoft XDE\10.0.18362.0\ します。

### <a name="account-tab"></a>[アカウント] タブ

[アカウント] タブでは、Microsoft アカウントでサインインにエミュレーターを構成できます。 これは、アカウントでサインインするユーザーを必要とする Api をテストするため便利です。  このオプションを切り替えることを完全に終了し、再起動を有効にする設定の HoloLens のエミュレーターが必要です。  このオプションが有効になっている場合、エミュレーターのそれ以降の起動時を依頼でサインイン、ユーザーと同様、初めて、HoloLens を開始します。  PC のキーボードを使用して、資格情報をすばやく入力するには、まず、シミュレーションのコントロール パネルで「シミュレーションのキーボードを使用する」オフにするか、キーボード設定のオンとオフを切り替えるをキーボード F4 キーを押します。

### <a name="optional-settings-tab"></a>オプションの設定 タブ

オプションの設定 タブを有効にするか、ハードウェア高速化されたグラフィックスを無効にするコントロールが表示されます。  ハードウェアの高速グラフィックスは、お客様の PC のグラフィックス アダプターのドライバーでサポートされている場合、既定で使用されます。  グラフィックス アダプターのドライバーが GPU PV をサポートしていない場合は、このオプションは表示されません。

### <a name="diagnostics-tab"></a>[診断] タブ

[診断] タブは、リンクの形式で、エミュレーターの IP アドレスを仮想 GPU の状態と共に Windows Device Portal に表示します。


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens の構造 (第 1 世代) エミュレーター

### <a name="main-window"></a>メイン ウィンドウ

エミュレーターを起動すると、HoloLens の OS を表示するウィンドウが表示されます。

![HoloLens のエミュレーターのメイン ウィンドウ](images/emulator-890px.png)

### <a name="toolbar"></a>ツール バー

メイン ウィンドウの右側には、エミュレーター ツールバーが表示されます。 ツールバーには、次のボタンが含まれています。
* ![ある閉じるアイコン](images/emulator-close.png)**閉じる**:エミュレーターを閉じます。
* ![最小化アイコン](images/emulator-minimize.png)**最小化**:エミュレーターのウィンドウを最小化します。
* ![人間の入力アイコン](images/emulator-control.png)**人間入力**:マウスとキーボードが人間をシミュレートするために使用される[エミュレーターへの入力](#basic-emulator-input)します。
* ![キーボードとマウス入力アイコン](images/emulator-input.png)**キーボードとマウス入力**:キーボードとマウスの入力として渡されます HoloLens OS に直接キーボードとマウスのイベント、Bluetooth キーボードとマウスを接続する場合と同じ。
* ![画面のアイコンに合わせる](images/emulator-fit.png)**画面に合わせる**:エミュレーターの画面に収まるようにします。
* ![[ズーム] アイコン](images/emulator-zoom.png)**ズーム**:大きくしたり小さく、エミュレーターを作成します。
* ![ヘルプ アイコン](images/emulator-help.png)**ヘルプ**:エミュレーターのヘルプを開きます。
* ![開いているデバイスのポータル アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。
* ![ツール アイコン](images/emulator-tools.png)**ツール**:開く、**追加ツール**ウィンドウ。

### <a name="simulation-tab"></a>シミュレーション タブ

内で、既定のタブ、**追加ツール**ウィンドウは、**シミュレーション**タブ。

![HoloLens のエミュレーターの追加ツール ウィンドウ](images/emulator-simulation-500px.png)

シミュレーションのタブには、エミュレーター内での HoloLens の OS を促進するために使用するシミュレートされたセンサーの現在の状態が表示されます。 シミュレーション タブの任意の値を合わせると、その値を制御する方法を説明するヒントが提供されます。

### <a name="room-tab"></a>ルーム タブ

エミュレーターでは、シミュレートされた「ルーム」から空間マッピング メッシュの形式で世界中の入力をシミュレートします。 このタブを使用して、どの部屋を既定のルームではなく読み込むを選択できます。

![HoloLens のエミュレーター 'ルーム' タブ](images/emulator-room-500px.png)

参照してください[ルームをシミュレートした](#simulated-rooms)詳細についてはします。

### <a name="account-tab"></a>[アカウント] タブ

[アカウント] タブでは、Microsoft アカウントでサインインにエミュレーターを構成できます。 これは、アカウントでサインインするユーザーを必要とする API をテストするため便利です。 このページで、ボックスをオンにした後でサインインすること、エミュレーターのそれ以降の起動時に尋ねます、HoloLens が開始されます、ユーザーが初めてと同様です。

## <a name="simulated-rooms"></a>シミュレートされたルーム

シミュレートされたルームは、複数の環境でアプリをテストするため便利です。 ルームのいくつかのエミュレーターが付属しています、%programfiles (x86) %\Windows Kits\10\Microsoft XDE の検索は、エミュレーションをインストールした後\\(バージョン) \Plugins\Rooms します。 すべてのこれらのルームは、HoloLens を使用して実際の環境でキャプチャされました。
* **DefaultRoom.xef** -小さなリビング ルーム、テレビ、コーヒー テーブルでは、2 つの sofas とします。 エミュレーターを起動すると、既定で読み込まれます。
* **Bedroom1.xef** -小規模の寝室、デスクとします。
* **Bedroom2.xef** -寝室クイーン サイズ ベッド、引き出しドレッサー、nightstands、および持ち込んでクローゼットを使用します。
* **GreatRoom.xef** -大きな空き領域優れたルーム リビング ルーム、レストランのテーブルおよびキッチンを使用します。
* **LivingRoom.xef** -、暖炉、ソファー、armchairs、リビング ルームおよびハードカバー花瓶とします。

シミュレーションのページを使用して、エミュレーターで使用する独自の部屋を記録することも、 [Windows Device Portal](using-the-windows-device-portal.md) HoloLens で (第 1 世代)。

エミュレーターでは、ホログラムをレンダリングして、ホログラムの背後にあるシミュレートされた部屋は表示されませんのみ表示されます。 これは、両方を表示する実際の HoloLens とは対照的ブレンドします。 HoloLens のエミュレーターのシミュレートされたルームが表示する場合は、シーン内の空間マッピングのメッシュを表示するために、アプリを更新する必要があります。

## <a name="troubleshooting"></a>トラブルシューティング

必要なエミュレーターのインストール中にエラーが表示可能性があります *「Visual Studio 2015 Update 1 と UWP ツール バージョン 1.2」* します。 このエラーの考えられる原因を次の 3 つあります。
* Visual Studio (Visual Studio 2019、Visual Studio 2017 または Visual Studio 2015 Update 1 またはそれ以降) の最新バージョンではありません。 これを修正するには、Visual Studio の最新リリースをインストールします。
* Visual Studio の最新バージョンがあることが、ユニバーサル Windows プラットフォーム (UWP) ツールがインストールされている必要はありません。 これは、Visual Studio のオプション機能です。

エミュレーターで、非-Pro、Enterprise、/教育 SKU の Windows のインストール エラーを表示もまたは HYPER-V 機能がいないかどうかに有効になっています。
* 参照してください、[システム要件](#hololens-emulator-system-requirements)要件の完全なセットを前の「します。
* システム上で HYPER-V の機能が有効であることを確認してください。

インストールが正常に完了したデプロイとデバッグのためのオプションとして、HoloLens のエミュレーターが表示されない場合は、次の点を確認してください。
* Visual Studio プロジェクト構成は、x86 (HoloLens の第 1 世代) または x86 または x64 (HoloLens 2 エミュレーター) に設定されます。
* Visual Studio 2019 を使用して、プロジェクトの構成でプラットフォーム ツールセットは v142 に設定されます。

インストールが正常に完了した場合は、Visual Studio には、HoloLens のエミュレーターを起動しようとしてエラーが表示されます。 は、次をやり直してください。
* Visual Studio を管理者として実行します。
* Visual Studio 2019 がインストールされている、だけ持っている場合は、hkey_local_machine \software\microsoft\windows Kits\Installed ルートにあるレジストリ値"KitsRoot10"が、32 ビットの Program Files フォルダーを指していることを確認 (例:"C:\Program Files (x86) \Windows キット\10")。  そうでない場合は、HoloLens のエミュレーターをアンインストールし、32 ビットの Program Files フォルダーへのレジストリ値を変更、HoloLens のエミュレーターを再インストールします。  この問題は、Visual Studio 2019 16.0.3 で対処されます。

場合は、エミュレーターでは、起動時に「無効なバイト エンコード」エラー ダイアログが表示されます。
* %Localappdata%\Microsoft\XDE\HCS 内のすべてのファイルを削除してからやり直してください。

Visual Studio でデバッグ ターゲット リストが空かどうか (たとえば、"Start"は、唯一のオプション) 上記すべてのトラブルシューティングの手順に従っているとします。
* %Localappdata%\Microsoft\VisualStudio の 'ConfigurationCache' フォルダーを削除\\<*インストール id*> \CoreCon し、もう一度やり直してください。

エミュレーターを開始するときに、システムがハングした場合は、エミュレーターのグラフィックス ハードウェア アクセラレータを無効にします。
* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 で"DisableGPU"という名前のレジストリ DWORD 値を作成し、その値を 1 に設定します。

## <a name="see-also"></a>関連項目
* [高度な HoloLens エミュレーターと Mixed Reality Simulator の入力](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens のエミュレーターのソフトウェアの履歴](hololens-emulator-archive.md)
* [Unity の空間マッピング](spatial-mapping-in-unity.md)
* [DirectX の空間マッピング](spatial-mapping-in-directx.md)
