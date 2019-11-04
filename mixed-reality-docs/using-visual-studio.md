---
title: Visual Studio を使用した配置とデバッグ
description: Visual Studio を使用して、HoloLens および Windows Mixed Reality 用のアプリをビルド、デバッグ、展開する方法について説明します。
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
keywords: Visual Studio, HoloLens, Mixed Reality, デバッグ, 配置
ms.openlocfilehash: 2b84183417a1bd4eaa90eef58bebe2b65966b933
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437310"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio を使用した配置とデバッグ

DirectX と Unity のどちらを使用して mixed reality アプリを開発する場合でも、Visual Studio を使用してデバッグと配置を行います。 このセクションでは、次のことについて説明します。
* Visual Studio を使用して HoloLens または Windows Mixed Reality のイマーシブヘッドセットにアプリケーションを展開する方法について説明します。
* Visual Studio に組み込まれている HoloLens エミュレーターを使用する方法。
* Mixed reality アプリをデバッグする方法。

## <a name="prerequisites"></a>前提条件
1. インストール手順について[は、「ツールのインストール](install-the-tools.md)」を参照してください。
2. Visual Studio で新しいユニバーサル Windows アプリプロジェクトを作成します。  HoloLens (第1世代) の場合は、Visual Studio 2017 以降を使用します。  Hololens 2 の場合は、Visual Studio 2019 16.2 以降を使用します。 C#とC++がサポートされています。 (または、「 [Unity でアプリを作成する」](holograms-100.md)の手順に従ってください)。

## <a name="enabling-developer-mode"></a>開発者モードを有効にする

まず、デバイスで**開発者モード**を有効にして、Visual Studio がそれに接続できるようにします。

### <a name="hololens"></a>HoloLens
1. HoloLens をオンにして、デバイスに配置します。
2. [ブルーム](system-gesture.md#bloom) ジェスチャを実行して、メイン メニューを開きます。
3. **[設定]** タイルを見つめ、[エアタップ](gaze-and-commit.md#composite-gestures)ジェスチャを実行します。 2 回目のエア タップを実行して、アプリを環境内に配置します。 配置すると、設定アプリが起動します。
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[Developer Mode]** (開発者モード) を有効にします。 これにより、 [Visual Studio から](using-visual-studio.md)HoloLens にアプリをデプロイできるようになります。
7. 省略可能: 下へスクロールし、**デバイスポータル**も有効にします。 これにより、web ブラウザーから HoloLens の[Windows デバイスポータル](using-the-windows-device-portal.md)に接続することもできます。

### <a name="windows-pc"></a>Windows PC

PC に接続されている Windows Mixed Reality ヘッドセットを使用している場合は、PC で**開発者モード**を有効にする必要があります。
1. **設定**に進む
2. **更新プログラムとセキュリティ**を選択する
3. **開発者向けの**選択
4. **開発者モード**を有効にし、選択した設定の免責事項を読み、[はい] をクリックして変更を確定します。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Wi-fi 経由でのアプリの展開 (第1世代)
1. Visual Studio で x86 ビルド構成 ![、アプリの**x86**ビルド構成を選択し](images/x86setting.png)
2. 配置ターゲット ドロップダウンメニューで **[リモートコンピューター]** を選択して、Visual Studio でリモートコンピューターの配置ターゲットを ![](images/remotemachinesetting.png)
3. およびC++ JavaScript プロジェクトの場合は、**プロジェクト > のプロパティ > 構成プロパティ** の デバッグ > ます。 プロジェクトC#の場合、接続を構成するためのダイアログボックスが自動的にポップアップ表示されます。
  」を参照します。 [**アドレス**または**コンピューター名**] フィールドに、デバイスの IP アドレスを入力します。 **[設定 > Network & Internet > 詳細オプション]** の下の HOLOLENS で ip アドレスを見つけます。または、Cortana "どのような ip アドレスがあるか" を質問することもできます。
  b. Visual Studio の [リモート接続] ダイアログ![[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定し](images/remotedeploy.png)
4. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)
5. PC から HoloLens にアプリを初めて展開するときに、PIN の入力を求められます。 下記の「**デバイスのペアリング**」の手順に従います。

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Wi-fi-HoloLens 2 でのアプリの展開
1. アプリの**ARM**または**ARM64**のビルド構成を選択してください。 Visual Studio の ARM64 ビルド構成 ![](images/arm64setting.png)
2. 配置ターゲット ドロップダウンメニューで **[リモートコンピューター]** を選択して、Visual Studio でリモートコンピューターの配置ターゲットを ![](images/remotemachinesetting_arm64.png)
3. およびC++ JavaScript プロジェクトの場合は、**プロジェクト > のプロパティ > 構成プロパティ** の デバッグ > ます。 プロジェクトC#の場合、接続を構成するためのダイアログボックスが自動的にポップアップ表示されます。
  」を参照します。 [**アドレス**または**コンピューター名**] フィールドに、デバイスの IP アドレスを入力します。 **[設定 > Network & Internet > 詳細オプション]** の下の HOLOLENS で ip アドレスを見つけます。または、Cortana "どのような ip アドレスがあるか" を質問することもできます。
  b. Visual Studio の [リモート接続] ダイアログ![[認証モード] を [**ユニバーサル (暗号化**されていないプロトコル)] に設定し](images/remotedeploy.png)
4. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)
5. PC から HoloLens にアプリを初めて展開するときに、PIN の入力を求められます。 下記の「**デバイスのペアリング**」の手順に従います。

HoloLens IP アドレスが変更された場合は、 **[プロジェクト > のプロパティ > 構成プロパティ]** の順に移動して、ターゲットコンピューターの ip アドレスを変更でき > デバッグ

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB HoloLens でのアプリの展開 (第1世代)
1. Visual Studio で x86 ビルド構成 ![、アプリの**x86**ビルド構成を選択し](images/x86setting.png)
2. 配置ターゲット ドロップダウンメニューで **[デバイス]** を選択して、Visual Studio で![デバイスをデプロイ](images/buildsettingsusbdeploy.png)
3. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)
4. PC から HoloLens にアプリを初めて展開するときに、PIN の入力を求められます。 下記の「**デバイスのペアリング**」の手順に従います。

## <a name="deploying-an-app-over-usb---hololens-2"></a>USB でのアプリの展開-HoloLens 2
1. アプリの**ARM**または**ARM64**のビルド構成を選択してください。 Visual Studio の ARM64 ビルド構成 ![](images/arm64setting.png)
2. 配置ターゲット ドロップダウンメニューで **[デバイス]** を選択して、Visual Studio で![デバイスをデプロイ](images/buildsettingsusbdeploy_arm64.png)
3. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)
4. PC から HoloLens にアプリを初めて展開するときに、PIN の入力を求められます。 下記の「**デバイスのペアリング**」の手順に従います。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>ローカル PC にアプリを展開する-イマーシブヘッドセット

PC または[Mixed reality シミュレーター](using-the-windows-mixed-reality-simulator.md)に接続する Windows Mixed reality イマーシブヘッドセットを使用する場合は、次の手順に従います。 このような場合は、単にローカル PC にアプリをデプロイして実行します。
1. アプリの**x86**または**x64**のビルド構成を選択します
2. 配置ターゲット ドロップダウンメニューで **ローカルコンピューター** を選択します。
3. [デバッグ] > を選択して**デバッグを開始**し、アプリをデプロイしてデバッグを開始します。

## <a name="pairing-your-device"></a>デバイスをペアリングする

Visual Studio から HoloLens に初めてアプリをデプロイするときに、PIN の入力を求められます。 HoloLens で、設定アプリを起動して PIN を生成し、**開発者向けの [Update >** ] にアクセスして、 **[ペアリング]** をタップします。 HoloLens に PIN が表示されます。Visual Studio でこの PIN を入力します。 ペアリングが完了したら、HoloLens で **[完了]** をタップしてダイアログを閉じます。 この PC は HoloLens とペアリングされているので、アプリを自動的に展開できます。 HoloLens にアプリを展開するために使用されるすべての後続 PC に対して、これらの手順を繰り返します。

HoloLens とペアリングされているすべてのコンピューターの組み合わせを解除するには、**設定** アプリを起動し、**開発者向けの更新プログラム >** にアクセスして、**クリア** をタップします。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens (第1世代) エミュレーターへのアプリのデプロイ
1. **[HoloLens エミュレーターがインストールされ](install-the-tools.md)** ていることを確認します。
2. アプリの**x86**ビルド構成を選択します。
Visual Studio での x86 ビルド構成の ![](images/x86setting.png)
3. 配置ターゲット ドロップダウンメニューで  **[HoloLens Emulator]** を選択し、Visual Studio の [エミュレーターターゲット] を![](images/deployemulator.png)
4. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>HoloLens 2 エミュレーターへのアプリのデプロイ
1. **[HoloLens エミュレーターがインストールされ](install-the-tools.md)** ていることを確認します。
2. アプリの**x86**または**x64**のビルド構成を選択します。
Visual Studio での x86 ビルド構成の ![](images/x86setting.png)
3. 配置ターゲット ドロップダウンメニューで  **[HoloLens 2 emulator]** を選択し、Visual Studio の [emulator target]![](images/deployemulator2.png)
4. [デバッグ **> 開始**] を選択して、アプリを配置し、デバッグを開始![Visual Studio でデバッグを行わずに開始](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens 用グラフィックスデバッガー (第1世代)

Visual Studio グラフィックス診断ツールは、Holographic アプリを作成して最適化するときに非常に役立ちます。 詳細については、 [MSDN の「Visual Studio グラフィックス診断](https://msdn.microsoft.com/library/hh315751.aspx)」を参照してください。

**グラフィックスデバッガーを起動するには**
1. 上記の手順に従って、デバイスまたはエミュレーターをターゲットにします。
2. **デバッグ > のグラフィックス > 診断の開始**
3. HoloLens で初めてこれを行うと、"アクセスが拒否されました" というエラーが発生することがあります。 HoloLens を再起動して、更新されたアクセス許可が有効になるようにしてから、もう一度やり直してください。

## <a name="profiling"></a>ルミ

Visual Studio プロファイリングツールを使用すると、アプリのパフォーマンスとリソースの使用を分析できます。 これには、CPU、メモリ、グラフィックス、およびネットワークの使用を最適化するためのツールが含まれます。 詳細については、 [MSDN の「デバッグなしの診断ツールの実行](https://msdn.microsoft.com/library/dn957936.aspx)」を参照してください。

**HoloLens でプロファイルツールを開始するには**
1. 上記の手順に従って、デバイスまたはエミュレーターをターゲットにします。
2. デバッグ **> 開始診断ツールデバッグなしで開始...**
3. 使用するツールを選択します
4. **[開始]** をクリック
5. HoloLens で初めてこれを行うと、"アクセスが拒否されました" というエラーが発生することがあります。 HoloLens を再起動して、更新されたアクセス許可が有効になるようにしてから、もう一度やり直してください。

## <a name="debugging-an-installed-or-running-app"></a>インストールされているアプリまたは実行中のアプリのデバッグ

Visual Studio を使用して、Visual Studio プロジェクトから配置せずにインストールされたユニバーサル Windows アプリをデバッグすることができます。 これは、インストールされているアプリケーションパッケージをデバッグする場合や、既に実行中のアプリをデバッグする場合に便利です。
1. [**デバッグ]-[その他のデバッグターゲット]-> [インストールされているアプリパッケージのデバッグ**] を >
2. イマーシブヘッドセットの場合は、HoloLens または**ローカルコンピューター**の**リモートコンピューター**ターゲットを選択します。
3. デバイスの**IP アドレス**を入力してください
4. **ユニバーサル**認証モードを選択する
5. このウィンドウには、実行中のアプリと非アクティブなアプリの両方が表示されます。 デバッグするものを選択します。
6. デバッグするコードの種類を選択します (マネージ、ネイティブ、混合)
7. [**アタッチ**または**開始**] をクリック

## <a name="see-also"></a>関連項目
* [ツールのインストール](install-the-tools.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [ユニバーサル Windows プラットフォーム (UWP) アプリのデプロイとデバッグ](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [開発用にデバイスを有効にする](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
