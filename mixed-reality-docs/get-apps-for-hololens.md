---
title: HoloLens 用アプリを入手します。
description: HoloLens、両方を Microsoft Store とのサイド ロード アプリ インストールについて説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: サイドロード、側の負荷、サイドローディング、ストア、uwp、アプリのインストール
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597554"
---
# <a name="get-apps-for-hololens"></a>HoloLens 用アプリを入手します。

、、Windows 10 デバイスとしては、HoloLens は多くの既存の UWP アプリケーションから、アプリ ストアとして HoloLens 専用に構築された新しいアプリをサポートします。 これらの上にすることもできますを[開発](development-overview.md)独自のアプリ、または、友人のインストールと!

## <a name="installing-apps"></a>アプリのインストール

これには、HoloLens に新しいアプリをインストールする 3 つの方法があります。 プライマリのメソッドは、Windows ストアから新しいアプリケーションをインストールになります。 ただし、デバイス ポータルを使用して、独自のアプリケーション インストールもまたはして Visual Studio からデプロイすることです。

### <a name="from-the-microsoft-store"></a>Microsoft Store から
1. 実行、[ブルーム](gestures.md#bloom)ジェスチャを開く、 [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)します。
2. ストア アプリを選択し、世界中にこのタイルを配置する をタップします。
3. ストア アプリが開いたら、任意の必要なアプリケーションを検索する検索バーを使用します。
4. 選択**取得**または**インストール**(購入が必要に可能性があります)、アプリケーションのページ。

### <a name="installing-an-application-package-with-the-device-portal"></a>デバイスのポータルを使用したアプリケーション パッケージをインストールします。
1. 接続を確立[デバイス ポータル](using-the-windows-device-portal.md)HoloLens のターゲットにします。
2. 移動し、**アプリ**左側のナビゲーション ページ。
3. **アプリ パッケージ**アプリケーションに関連付けられている .appx ファイルを参照します。
  >[!IMPORTANT]
  >関連付けられているすべての依存関係と証明書ファイルを参照してください。

4. クリックして**移動**します。

![Microsoft HoloLens で Windows Device Portal でアプリのフォームをインストールします。](images/deviceportal-appmanager.jpg)<br>
Windows Device Portal を使用して、HoloLens にアプリをインストールするには

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Microsoft Visual Studio 2015 からのデプロイ
1. アプリの Visual Studio ソリューション (.sln ファイル) を開きます。
2. プロジェクトの**プロパティ**します。
3. 次のビルド構成を選択します。マスター/x86/リモート マシン。
4. リモート コンピューターを選択するとします。
   * 確認アドレス ポイント HoloLens の WiFi の IP アドレスにします。
   * ユニバーサル (暗号化されていないプロトコル) への認証を設定します。
5. ソリューションをビルドします。
6. をクリックして、**リモート マシン**HoloLens を開発用 PC からアプリをデプロイするボタンをクリックします。 HoloLens の既存のビルドを既にがある場合は、この新しいバージョンを再インストールするには、[はい] を選択します。<br>
  ![Visual Studio での Microsoft HoloLens にアプリをリモート マシンのデプロイ](images/vs2015-remotedeployment.jpg)<br>
7. アプリケーションはインストールし、自動、HoloLens で起動します。
