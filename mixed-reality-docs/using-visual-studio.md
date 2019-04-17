---
title: Visual Studio を使用してデプロイをデバッグします。
description: ビルド、デバッグ、および HoloLens と Visual Studio を使用して Windows Mixed Reality アプリをデプロイする方法。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio、HoloLens、Mixed Reality は、デバッグ、デプロイ.
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601371"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio を使用してデプロイをデバッグします。

複合現実アプリを開発する DirectX または Unity を使用するかどうかは Visual Studio のデバッグおよび展開するために使用します。 このセクションでは、次の説明は。
* HoloLens や Windows Mixed Reality イマーシブ ヘッドセット Visual Studio を使用するアプリケーションをデプロイする方法。
* Visual Studio に組み込まれている HoloLens のエミュレーターを使用する方法。
* 複合現実アプリをデバッグする方法。

## <a name="prerequisites"></a>前提条件
1. 参照してください[ツールをインストールする](install-the-tools.md)インストール手順についてはします。
2. Visual Studio 2015 Update 1 または Visual Studio 2017 では、新しいユニバーサル Windows アプリ プロジェクトを作成します。 C#、 C++、JavaScript のプロジェクトすべてサポートされます。 (または、指示に従って、 [Unity でビルドをアプリの作成](holograms-100.md))。

## <a name="enabling-developer-mode"></a>開発者モードを有効にする

有効にすると開始**開発者モード**Visual Studio が接続できるようにデバイスにします。

### <a name="hololens"></a>HoloLens
1. HoloLens を有効にし、デバイス上に配置します。
2. [ブルーム](gestures.md#bloom) ジェスチャを実行して、メイン メニューを開きます。
3. 見つめます、**設定**タイルし、実行、[エア タップ](gestures.md#air-tap)ジェスチャ。 2 回目のエア タップを実行して、アプリを環境内に配置します。 配置すると、設定アプリが起動します。
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[Developer Mode]** (開発者モード) を有効にします。 こうと、 [Visual Studio からアプリを展開](using-visual-studio.md)HoloLens にします。
7. 省略可能: 下へスクロールし、有効にすることも**デバイス ポータル**します。 接続することを許可するがこの、 [Windows Device Portal](using-the-windows-device-portal.md) web ブラウザーから、HoloLens にします。

### <a name="windows-pc"></a>Windows PC

お使いの PC に接続されている Windows Mixed Reality ヘッドセットを使用して有効にした**開発者モード**PC にします。
1. 移動して**設定**
2. 選択**更新とセキュリティ**
3. 選択**開発者向け**
4. 有効にする**開発者モード**、選択した設定の免責事項を読んで、変更を確定するには、[はい] をクリックします。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>HoloLens Wi-fi 経由でアプリを展開する (第 1 世代)
1. 選択、 **x86**アプリの構成をビルド![x86 ビルドの Visual Studio での構成](images/x86setting.png)
2. 選択**リモート マシン**デプロイ ターゲット ドロップダウン メニューで![Visual Studio でのリモート コンピューターの配置ターゲット](images/remotemachinesetting.png)
3. C++および JavaScript プロジェクトの場合に移動して**プロジェクト > プロパティ > 構成プロパティ > デバッグ**します。 C#プロジェクトは、ダイアログがポップアップに自動的に接続を設定します。
  a.  デバイスの IP アドレスを入力して、**アドレス**または**マシン名**フィールド。 下、HoloLens の IP アドレスを調べる**設定 > ネットワークとインターネット > 高度なオプション**Cortana をもらうことができます、"What is my IP address?"または
  b.  認証モードを設定**ユニバーサル (暗号化されていないプロトコル)**![Visual Studio でのリモート接続 ダイアログ](images/remotedeploy.png)
4. 選択**デバッグ > デバッグを開始**アプリを展開およびデバッグを開始する![デバッグなしで開始 Visual Studio で](images/deploynodebugging.png)
5. 初めて、PC から、HoloLens にアプリを展開するは促さ PIN の。 に従って、**デバイスをペアリング**以下の手順。

移動して、ターゲット マシンの IP アドレスを変更するには、HoloLens の IP アドレスが変更された場合**プロジェクト > プロパティ > 構成プロパティ > デバッグ**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB - HoloLens でアプリを配置する (第 1 世代)
1. 選択、 **x86**アプリの構成をビルド![x86 ビルドの Visual Studio での構成](images/x86setting.png)
2. 選択**デバイス**デプロイ ターゲット ドロップダウン メニューで![Visual Studio でのデバイスのデプロイ](images/buildsettingsusbdeploy.png)
3. 選択**デバッグ > デバッグを開始**アプリを展開およびデバッグを開始する![デバッグなしで開始 Visual Studio で](images/deploynodebugging.png)
4. 初めて、PC から、HoloLens にアプリを展開するは促さ PIN の。 に従って、**デバイスをペアリング**以下の手順。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>イマーシブ ヘッドセット - ローカル PC にアプリを展開します。

お使いの PC に接続する Windows Mixed Reality イマーシブ ヘッドセットを使用する場合は、次の手順をに従ってまたは[Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)します。 このような場合に、デプロイし、ローカル PC でアプリを実行します。
1. 選択、 **x86**または**x64**ビルド アプリの構成
2. 選択**ローカル マシン**で、デプロイ ターゲット ドロップダウン メニュー
3. 選択**デバッグ > デバッグを開始**アプリを展開およびデバッグを開始するには

## <a name="pairing-your-device---hololens-1st-gen"></a>HoloLens - デバイスをペアリング (第 1 世代)

初めて、HoloLens、するには、Visual Studio からアプリを展開するは促さ PIN の。 移動して、設定アプリを起動することで、PIN を生成、HoloLens の**更新 > 開発者向け**をタップする**ペア**します。 PIN は、HoloLens; に表示されます。Visual Studio では、この PIN を入力します。 タップしてペアリングが完了したら、**完了**上、HoloLens ダイアログ ボックスを閉じます。 この PC は今すぐ、HoloLens と組み合わせて使用し、アプリを自動的に展開することができます。 HoloLens にアプリを展開するために使用するすべての後続の PC の次の手順を繰り返します。

解除ペアを使用すると、ペアになっているが、すべてのコンピューターから、HoloLens の起動、**設定**アプリに移動して**更新 > 開発者向け**をタップする**クリア**。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens にアプリを展開する (第 1 世代) エミュレーター
1. 必ず確保 **[HoloLens のエミュレーターがインストールされている](install-the-tools.md)** します。
2. 選択、 **x86**アプリの構成をビルドします。
![x86 ビルドの Visual Studio での構成](images/x86setting.png)
3. 選択**HoloLens のエミュレーター**デプロイ ターゲット ドロップダウン メニューで![Visual Studio でのエミュレーターのターゲット](images/deployemulator.png)
4. 選択**デバッグ > デバッグを開始**アプリを展開およびデバッグを開始する![デバッグなしで開始 Visual Studio で](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>グラフィックス デバッガー

Visual Studio グラフィックス診断ツールは、書き込みおよび Holographic アプリを最適化するときに非常に便利です。 参照してください[msdn の Visual Studio グラフィックス診断](https://msdn.microsoft.com/library/hh315751.aspx)の完全な詳細情報。

**グラフィックス デバッガーを起動するには**
1. デバイスまたはエミュレーターを対象には、上記の手順に従ってください。
2. 移動して**デバッグ > グラフィックス > 診断の開始**
3. 初めて、HoloLens でこれを行う「アクセスが拒否されました」エラーが発生する可能性があります。 更新されたアクセス許可を反映し、もう一度お試し、HoloLens を再起動します。

## <a name="profiling"></a>プロファイリング

Visual Studio プロファイリング ツールを使用すると、アプリのパフォーマンスとリソース使用量を分析できます。 これには、CPU、メモリ、グラフィックスを最適化し、ネットワークの使用のツールが含まれています。 参照してください[なし、MSDN でのデバッグ診断ツールの実行](https://msdn.microsoft.com/library/dn957936.aspx)の完全な詳細情報。

**HoloLens でプロファイリング ツールを開始するには**
1. デバイスまたはエミュレーターを対象には、上記の手順に従ってください。
2. 移動して**デバッグ > デバッグなしで診断ツールを開始しています.**
3. 使用するツールを選択します。
4. クリックして**開始**
5. 初めて、HoloLens でこれを行う「アクセスが拒否されました」エラーが発生する可能性があります。 更新されたアクセス許可を反映し、もう一度お試し、HoloLens を再起動します。

## <a name="debugging-an-installed-or-running-app"></a>インストールまたは実行中のアプリのデバッグ

Visual Studio を使用して、Visual Studio プロジェクトからデプロイせずにインストールされているユニバーサル Windows アプリをデバッグすることができます。 これは、インストールされているアプリ パッケージをデバッグする場合、または既に実行されているアプリをデバッグする場合に役立ちます。
1. 移動して**デバッグ]、[その他のデバッグ ターゲットにインストールされているアプリケーション パッケージのデバッグ]-> [**
2. 選択、**リモート マシン**HoloLens のターゲットまたは**ローカル マシン**イマーシブ ヘッドセットをします。
3. デバイスの入力**IP アドレス**
4. 選択、**ユニバーサル**認証モード
5. ウィンドウには、実行中と非アクティブの両方のアプリが表示されます。 希望するものをデバッグする 1 つを選択します。
6. (マネージ、ネイティブ、Mixed) をデバッグするコードの種類を選択します。
7. クリックして**アタッチ**または**開始**

## <a name="see-also"></a>関連項目
* [ツールをインストールします。](install-the-tools.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [展開して、ユニバーサル Windows プラットフォーム (UWP) アプリのデバッグ](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [開発用にデバイスを有効にします。](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
