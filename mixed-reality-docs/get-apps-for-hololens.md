---
title: HoloLens 用アプリを取得する
description: Microsoft Store とサイドローディングを使用して、HoloLens 用のアプリをインストールする方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: サイドロード、サイドロード、サイドロード、ストア、uwp、アプリ、インストール
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522541"
---
# <a name="get-apps-for-hololens"></a>HoloLens 用アプリを取得する

Windows 10 デバイスとして、HoloLens は、アプリストアからの多くの既存の UWP アプリケーションだけでなく、HoloLens 専用に構築された新しいアプリもサポートしています。 これらに加えて、独自のアプリや友人のアプリを[開発](development-overview.md)してインストールすることが必要になる場合もあります。

## <a name="installing-apps"></a>アプリのインストール

HoloLens に新しいアプリをインストールするには、次の3つの方法があります。 主要な方法は、Windows ストアから新しいアプリケーションをインストールすることです。 ただし、デバイスポータルを使用するか、Visual Studio から展開することで、独自のアプリケーションをインストールすることもできます。

### <a name="from-the-microsoft-store"></a>Microsoft Store から
1. [ブルーム](gestures.md#bloom)ジェスチャを実行して [[スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu)を開きます。
2. ストアアプリを選択し、タップして、このタイルを世界に配置します。
3. ストアアプリが開いたら、検索バーを使用して目的のアプリケーションを探します。
4. アプリケーションのページで **[取得]** または **[インストール]** を選択します (購入が必要な場合があります)。

### <a name="installing-an-application-package-with-the-device-portal"></a>デバイスポータルを使用したアプリケーションパッケージのインストール
1. [デバイスポータル](using-the-windows-device-portal.md)からターゲット HoloLens への接続を確立します。
2. 左側のナビゲーションで、 **[アプリ]** ページに移動します。
3. **[アプリパッケージ]** の下で、アプリケーションに関連付けられている .appx ファイルを参照します。
  >[!IMPORTANT]
  >関連する依存関係および証明書ファイルを必ず参照してください。

4. **[検索]** をクリックします。

![Microsoft HoloLens の Windows デバイスポータルでアプリフォームをインストールする](images/deviceportal-appmanager.jpg)<br>
Windows デバイスポータルを使用して HoloLens にアプリをインストールする

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Microsoft Visual Studio 2015 からの展開
1. アプリの Visual Studio ソリューション (.sln ファイル) を開きます。
2. プロジェクトの**プロパティ**を開きます。
3. 次のビルド構成を選択します。マスター/x86/リモートコンピューター。
4. [リモートコンピューター] を選択した場合:
   * アドレスが HoloLens の WiFi IP アドレスを指していることを確認します。
   * 認証を Universal (暗号化されていないプロトコル) に設定します。
5. ソリューションをビルドします。
6. **[リモートコンピューター]** ボタンをクリックして、開発用 PC から HoloLens にアプリをデプロイします。 HoloLens に既存のビルドが既に存在する場合は、[はい] を選択して、この新しいバージョンを再インストールします。<br>
  ![Visual Studio でのアプリの Microsoft HoloLens へのリモートコンピューターの展開](images/vs2015-remotedeployment.jpg)<br>
7. アプリケーションが HoloLens にインストールされ、自動的に起動します。
