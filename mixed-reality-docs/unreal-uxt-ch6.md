---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアルのパート 6
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519970"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.デバイスまたはエミュレーターへのパッケージ化とデプロイ

このセクションでは、HoloLens 2 のデバイスまたはエミュレーターで実行するようにアプリを準備する手順について説明します。 デバイスをお持ちの場合は、コンピューターからデバイスにストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。 デバイスがない場合は、アプリをパッケージ化してエミュレーターで実行する必要があります。 

## <a name="objectives"></a>目標

* [デバイスのみ] アプリのホログラフィック リモート処理によってアプリを HoloLens 2 にストリーミングする
* アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする

## <a name="device-only-stream"></a>[デバイスのみ] ストリーミング

1.  Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。

2.  **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。 [Holographic Remoting]\(ホログラフィック リモート処理\) セクションで、チェック ボックスをオンにしてリモート処理を有効にし、エディターを再起動します。

3.  デバイスの IP アドレスを入力し、[Connect]\(接続\) をクリックします。

4.  接続後、UE4 エディターで [Play]\(再生\) ボタンの右側にあるドロップダウン矢印をクリックし、[VR Preview]\(VR プレビュー\) を選択します。

## <a name="package-and-deploy-your-app"></a>アプリのパッケージ化とデプロイ 

>[!NOTE]
>HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。 これを行うには、Epic Games Launcher の **[ライブラリ]** タブに移動します。 **[起動]** の横にあるドロップダウン矢印を選択し、 **[オプション]** を選択します。 **[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。 
>![プロジェクト設定 - 説明](images/unreal-uxt/6-installationoptions.PNG)

1.  **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。 **[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクトに名前を付けます。 **[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(パブリッシャー\) > [Company Distinguished Name]\(企業識別名\)** に「CN={INSERT COMPANY NAME}」を入力します。 これらのフィールドのいずれかを空白のままにすると、エラーが発生します。 

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  **[Platforms]\(プラットフォーム\) > [HoloLens]** で、どれをターゲットにするかに応じて [Emulation]\(エミュレーション\)、[Device]\(デバイス\)、またはその両方を選択します。

3.  **[Packaging]\(パッケージ化\)** セクションの **[Signing Certificate]\(証明書に署名\)** で、 **[Generate new]\(新規生成\)** ボタンをクリックして新しい署名証明書を生成します。 メイン ウィンドウに戻ります。

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  **[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。 パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。 

5.  アプリが正常にパッケージ化されたら、**Windows デバイス ポータル**を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリの展開\)** セクションを見つけます。

6.  **[参照]** をクリックし、**ChessApp.appxbundle** ファイルに移動します。 **[開く]** をクリックします。 

    * デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。 次のダイアログで、適切な VCLibs appx ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。 

7.  **[Install]** (インストール) をクリックします。

このチュートリアルを終了していただき、ありがとうございます。  