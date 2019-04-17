---
title: HoloLens のエミュレーターを使用します。
description: HoloLens のエミュレーターを使用して、物理 HoloLens なし、PC 上の複合現実アプリをテストできます。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、エミュレーター
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604101"
---
# <a name="using-the-hololens-emulator"></a>HoloLens のエミュレーターを使用します。

HoloLens のエミュレーターは、HoloLens の開発ツールセットが付属して物理 HoloLens なし、PC で holographic のアプリをテストすることができます。 エミュレーターでは、HYPER-V 仮想マシンを使用します。 通常、HoloLens のセンサーによって読み取られる人間と環境の入力は、キーボード、マウス、または Xbox コント ローラーを使用して代わりにシミュレートします。 アプリでは、エミュレーターで実行するように変更する必要はありませんを実際の HoloLens で実行されていないことがわからない。

デスクトップ Pc の Windows Mixed Reality 没入型 (VR) ヘッドセット アプリやゲームを開発する場合、チェック アウト、 [Windows Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)、代わりにデスクトップ ヘッドセットをシミュレートすることができます。

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

## <a name="installing-the-hololens-emulator"></a>HoloLens のエミュレーターをインストールします。

ダウンロード、 [HoloLens (第 1 世代) エミュレーターおよび holographic プロジェクト テンプレート](https://go.microsoft.com/fwlink/?linkid=2065980)します。

HoloLens のエミュレーターの以前のビルドのについて、 [HoloLens のエミュレーターのアーカイブ](hololens-emulator-archive.md)ページ。

### <a name="hololens-emulator-system-requirements"></a>HoloLens のエミュレーターのシステム要件

HoloLens のエミュレーターでは、HYPER-V に基づいており、ハードウェア高速グラフィックス用の RemoteFx を使用します。 エミュレーターを使用するには、PC は、これらのハードウェア要件を満たしていることを確認します。
* 64 ビットの Windows 10 Pro、Enterprise、または教育 
    >[!NOTE]
    >Windows 10 Home エディションは、HYPER-V または HoloLens のエミュレーターをサポートしていません
* 64 ビット CPU
* CPU と 4 コア (または複数の Cpu と 4 コアの合計)
* 8 GB 以上の RAM
* 次の機能がある必要があります、BIOS で[サポートされていて有効](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * ハードウェア支援による仮想化
   * Second Level Address Translation (SLAT)
   * ハードウェアベースのデータ実行防止 (DEP)
* GPU の要件 (エミュレーターでサポートされていない GPU では、機能しますが、大幅に遅くなります)
   * DirectX 11.0 以降
   * WDDM 1.2 ドライバーまたはそれ以降

システムが、上記の要件を満たす場合**システムに"HYPER-V"機能が有効になっているか確認してください** コントロール パネル-> プログラム の プログラムと機能の Windows 機能の有効化-> または-> オフことを確認"ハイパー-V"が正常にエミュレーターのインストールの選択されています。

### <a name="installation-troubleshooting"></a>インストールのトラブルシューティング

必要なエミュレーターのインストール中にエラーが表示可能性があります *「Visual Studio 2015 Update 1 と UWP ツール バージョン 1.2」* します。 このエラーの考えられる原因を次の 3 つあります。
* Visual Studio (Visual Studio 2017 または Visual Studio 2015 Update 1 またはそれ以降) の最新バージョンではありません。 これを修正するには、Visual Studio の最新リリースをインストールします。
* Visual Studio の最新バージョンがあることが、ユニバーサル Windows プラットフォーム (UWP) ツールがインストールされている必要はありません。 これは、Visual Studio のオプション機能です。

エミュレーターで、非-PRO、Enterprise、/教育 SKU の Windows のインストール エラーを表示もまたは HYPER-V 機能がいないかどうかに有効になっています。
* 参照してください、[システム要件](#hololens-emulator-system-requirements)要件の完全なセットを前の「します。
* システム上で HYPER-V の機能が有効であることを確認してください。

## <a name="deploying-apps-to-the-hololens-emulator"></a>HoloLens のエミュレーターにアプリを展開します。

1. Visual Studio 2015 でアプリ ソリューションを読み込みます。
    >[!NOTE]
    >Unity を使用する場合は、Unity からプロジェクトをビルドし、通常どおり Visual Studio に、作成されたソリューションを読み込みます。
2. プラットフォームに設定されていることを確認**x86**します。
3. 選択、 **HoloLens のエミュレーター**デバッグのターゲット デバイスとして。
4. 移動して**デバッグ > [デバッグ開始]** またはキーを押します**F5**エミュレーターを起動してデバッグ用のアプリをデプロイします。

エミュレーターは、最初に起動するときに起動する、1 分以上かかる場合があります。 開いたままにしておく、エミュレーター、デバッグ セッション中に実行中のエミュレーターにアプリをすばやくデプロイできるようにすることをお勧めします。

## <a name="basic-emulator-input"></a>基本的なエミュレーターの入力

エミュレーターの制御は、多くの一般的な 3 D ビデオ ゲームによく似ています。 入力オプションは、キーボード、マウス、または Xbox コント ローラーを使用できます。 エミュレーターを制御するには、ソックスを着けずに、HoloLens のシミュレートされたユーザーの操作をリダイレクトします。 周囲のシミュレートされたユーザーと、エミュレーターで実行されているアプリが実際のデバイスでこれらと同じように応答するアクションに移動します。
* **転送で、左、について説明し、右**-、W を使用して、キーボード、または Xbox コント ローラーでは、左側のスティック A、S、D キー。
* **検索、下、左、および右**-キーボード、または Xbox コント ローラーでは、適切なスティック上方向キーを使用 をクリックし、マウスをドラッグします。
* **エア タップ ジェスチャ**- マウスを右クリックし、キーボードの Enter キーを押してまたは Xbox コント ローラーでは、[A] ボタンを使用します。
* **ジェスチャを咲かせること**- には、キーボードの Windows キーまたは F2 キーを押して、または Xbox コント ローラーの B ボタンを押します。
* **スクロールの移動を渡す**- Alt キーを押しながらマウスの右ボタンを押しながらとアップ/ダウン、マウスをドラッグまたは Xbox コント ローラーで、適切なトリガーとボタンを押し、適切なスティックを上下に移動します。

## <a name="anatomy-of-the-hololens-emulator"></a>HoloLens のエミュレーターの構造

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

![HoloLens のエミュレーター ' 追加ツール ウィンドウ](images/emulator-simulation-500px.png)

シミュレーションのタブには、エミュレーター内での HoloLens の OS を促進するために使用するシミュレートされたセンサーの現在の状態が表示されます。 シミュレーション タブの任意の値を合わせると、その値を制御する方法を説明するヒントが提供されます。

### <a name="room-tab"></a>ルーム タブ

エミュレーターでは、シミュレートされた「ルーム」から空間マッピング メッシュの形式で世界中の入力をシミュレートします。 このタブを使用して、どの部屋を既定のルームではなく読み込むを選択できます。

![HoloLens のエミュレーター 'ルーム' タブ](images/emulator-room-500px.png)

シミュレートされたルームは、複数の環境でアプリをテストするため便利です。 ルームのいくつかのエミュレーターが付属していて、%programfiles(x86) %\Program Files (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 検索は、エミュレーションをインストールするとします。 すべてのこれらのルームは、HoloLens を使用して実際の環境でキャプチャされました。
* **DefaultRoom.xef** -小さなリビング ルーム、テレビ、コーヒー テーブルでは、2 つの sofas とします。 エミュレーターを起動すると、既定で読み込まれます。
* **Bedroom1.xef** -小規模の寝室、デスクとします。
* **Bedroom2.xef** -寝室クイーン サイズ ベッド、引き出しドレッサー、nightstands、および持ち込んでクローゼットを使用します。
* **GreatRoom.xef** -大きな空き領域優れたルーム リビング ルーム、レストランのテーブルおよびキッチンを使用します。
* **LivingRoom.xef** -、暖炉、ソファー、armchairs、リビング ルームおよびハードカバー花瓶とします。

シミュレーションのページを使用して、エミュレーターで使用する独自の部屋を記録することも、 [Windows Device Portal](using-the-windows-device-portal.md) HoloLens にします。

エミュレーターでは、ホログラムをレンダリングして、ホログラムの背後にあるシミュレートされた部屋は表示されませんのみ表示されます。 これは、両方を表示する実際の HoloLens とは対照的ブレンドします。 HoloLens のエミュレーターのシミュレートされたルームが表示する場合は、シーン内の空間マッピングのメッシュを表示するために、アプリを更新する必要があります。

### <a name="account-tab"></a>[アカウント] タブ

[アカウント] タブでは、Microsoft アカウントでサインインにエミュレーターを構成できます。 これは、アカウントでサインインするユーザーを必要とする API をテストするため便利です。 このページで、ボックスをオンにした後でサインインすること、エミュレーターのそれ以降の起動時に尋ねます、HoloLens が開始されます、ユーザーが初めてと同様です。

## <a name="see-also"></a>関連項目
* [HoloLens のエミュレーターと Mixed Reality シミュレーターの高度な入力](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens のエミュレーターのソフトウェアの履歴](hololens-emulator-archive.md)
* [Unity での空間のマッピング](spatial-mapping-in-unity.md)
* [DirectX での空間のマッピング](spatial-mapping-in-directx.md)
