---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330241"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.デバイスまたはエミュレーターへのパッケージ化とデプロイ

## <a name="overview"></a>概要

前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。 この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。 HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。 デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。 このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。

## <a name="objectives"></a>目標

* [デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする
* アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする

## <a name="device-only-streaming"></a>[デバイスのみ] ストリーミング
この場合、[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。 これは、リモート処理ホスト アプリが HoloLens から入力データ ストリームを受け取り、仮想イマーシブ ビューでコンテンツをレンダリングし、Wi-Fi 経由でコンテンツ フレームを HoloLens にストリームするという仕組みになっています。 ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。 

チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。

1.  Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。

2.  **[編集] > [プロジェクトの設定]** に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。

3.  エディターを再起動し、[デバイスの IP アドレスを検索](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi)して入力し、 **[接続]** をクリックします。

接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。 これにより、VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。 

## <a name="packaging-and-deploying-the-app"></a>アプリのパッケージ化とデプロイ 

>[!NOTE]
>HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。 
>- Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。 
>- **[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。 
>![プロジェクト設定 - 説明](images/unreal-uxt/6-installationoptions.PNG)

1.  **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。 
    * **[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。 
    * **[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(パブリッシャー\) > [Company Distinguished Name]\(企業識別名\)** に「**CN={INSERT COMPANY NAME}** 」を追加します。

> [!IMPORTANT]
> これらのフィールドのいずれかを空白のままにすると、エラーが発生します。 

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  **[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。

3.  **[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックし、メイン ウィンドウに戻ります。

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  **[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。 
    * パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。 

5.  アプリがパッケージ化されたら、[Windows デバイス ポータル](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。

6.  **[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。 

    * デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。 
    * 次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。 これらのファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。

7.  **[Install]** (インストール) をクリックします。
    * これで、 **[すべてのアプリ]** に移動して、新しくインストールされたアプリをタップして実行するか、**Windows デバイス ポータル**から直接アプリを起動できます。 

お疲れさまでした。 HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。 ただし、これは目的地ではありません。 MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。 これらの機能の詳細については、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を参照してください。