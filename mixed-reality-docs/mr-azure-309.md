---
title: MR と Azure 309 - Application insights
description: このコースでは、複合現実のアプリケーション内でユーザーの行動に関する Azure の Application Insights サービスを使用して、分析情報を収集する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、application insights、没入型、hololens、vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694568"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR と Azure 309:Application insights

![最終的な製品-開始](images/AzureLabs-Lab309-00.png)

このコースではユーザーの行動に関する分析情報を収集する Azure Application Insights API を使用して複合現実のアプリケーションに Application Insights の機能を追加する方法についてはします。

Application Insights は開発者にはアプリケーションから分析情報を収集し、使いやすいポータルから管理できるよう、Microsoft サービスです。 分析は、カスタム情報を収集するパフォーマンスから設定を指定できます。 詳細については、次を参照してください。、 [Application Insights のページ](https://azure.microsoft.com/services/application-insights/)します。

このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。

1.  された様子を確認し、シーン内を移動するユーザーを許可します。
2.  Analytics への送信をトリガー、 *Application Insights サービス*、視線の先およびシーン内のオブジェクトの近接度を使用しています。
3.  アプリは、サービスは、過去 24 時間内で、ユーザーが最もに近づくとオブジェクトがされている情報をフェッチ時に呼び出すこともします。 そのオブジェクトには、緑色にその色が変化します。

このコースでは、Unity に基づくサンプル アプリケーションに Application Insights サービスで、結果を取得する方法を説明します。 最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 309:Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。 コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。 HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- (組み込みのマイクとスピーカー、ヘッドセットはされていない) 場合は、内蔵マイクでヘッドフォン
- Azure のセットアップと Application Insights のデータ取得のインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。

> [!WARNING] 
> しようとするデータを対応する*Application Insights*時間がかかり、患者があるためです。 サービスが、データを受信したかどうかにチェックする場合は、チェック アウト[14 章](#chapter-14---the-application-insights-service-portal)ポータルに移動する方法を説明するされます。

## <a name="chapter-1---the-azure-portal"></a>第 1 章 - Azure Portal

使用する*Application Insights*、作成および構成する必要があります、 *Application Insights サービス*Azure portal でします。

1.  [Azure ポータル](https://portal.azure.com) にログインします。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して*Application Insights*、 をクリック**Enter**します。

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  右側に新しいページがの説明を入力、 *Azure Application Insights*サービス。 このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  クリックすると**作成**:

    1.  必要な挿入**名前**このサービス インスタンス。

    2.  として**アプリケーションの種類**、**全般**します。

    3.  適切な選択**サブスクリプション**します。

    4.  選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5.  選択、**場所**します。

    6.  また、このサービスに適用される条件を理解したことを確認する必要があります。

    7.  **[作成]** を選択します。

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 実施する、新しい*Application Insights サービス*インスタンス。

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  この web ページを開いたままにして簡単にアクセスでき、ここに戻り、収集されたデータを表示するには、多くの場合。

    > [!IMPORTANT]
    > Application Insights を実装するには次の 3 つ (3) 特定値を使用する必要があります。**インストルメンテーション キー**、**アプリケーション ID**、および**API キー**します。 次のとおり、サービスからこれらの値を取得する方法が表示されます。 空白でこれらの値をメモしておきます*メモ帳*ページのコードですぐに使用するがあるためです。

9.  検索する、**インストルメンテーション キー**、サービスの機能の一覧を下までスクロールし、をクリックする必要があります**プロパティ**、表示されるタブが表示されます、**サービス キー**します。

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. 少し下**プロパティ**、検索は**API アクセス**、 をクリックする必要があります。 右側にパネルを提供、**アプリケーション ID**アプリの。

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. **アプリケーション ID**パネル をクリックします**API キーの作成**、これが表示されます、 *API キーの作成*パネル。

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. ここで開く内*API キーの作成*パネルで、説明を入力および**3 つのボックスをオンに**。

13. クリックして**キー生成**します。 **API キー**が作成され、表示されます。 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > これは、唯一の時間、**サービス キー**が表示されます、ようにして今すぐそのコピーを作成します。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章 - Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-11.png)

2.  Unity プロジェクト名を指定する必要がありますこれで挿入**MR\_Azure\_アプリケーション\_Insights**します。 必ず、*テンプレート*に設定されている**3D**します。 設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-12.png)

3.  既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。 移動して**編集\>設定**し、新しいウィンドウに移動**外部ツール**します。 変更 **External Script Editor** に **Visual Studio 2017** します。 閉じる、**設定**ウィンドウ。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-13.png)

4.  次に移動**ファイル\>Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-14.png)

5.  移動して**ファイル\>Build Settings**ことを確認してください。

    1.  **デバイスを対象に**に設定されている**任意のデバイス**

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2.  **ビルドの種類**に設定されている**D3D**

    3.  **SDK**に設定されている**インストールされている最新**

    4.  **ビルドおよび実行**に設定されている**ローカル マシン**

    5.  シーンを保存し、ビルドに追加します。

        1.  これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-15.png)

        2. 任意の将来のシーンとこれには、新しいフォルダーを作成し、をクリックして、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-16.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名:* テキスト フィールドに「 **ApplicationInsightsScene**、順にクリックします**を保存**.

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-17.png)

6.  設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

7.  **Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-18.png)

8. このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **Scripting** **ランタイム バージョン**する必要があります**試験的 (.NET 4.6 Equivalent)** エディターを再起動する必要があるします。

        2.  **バックエンドの scripting**べき **.NET**

        3.  **API の互換性レベル**べき **.NET 4.6**

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-19.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**     

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-20.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行の設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed RealitySDK**が追加されます。

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab309-21.png)

9.  戻り**Build Settings**、 **UnityC#プロジェクト**が不要になったグレー; これの横にあるチェック ボックスをオンにします。

10.  ビルド設定ウィンドウを閉じます。

11.  シーンとプロジェクトを保存 (**ファイル** > **シーン保存/file** > **プロジェクト保存**)。


## <a name="chapter-3---import-the-unity-package"></a>第 3 章 - Unity パッケージのインポート

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[309.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)します。 [次へ] の章から Dll が含まれます。 インポートの後から引き続き[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)します。

> [!IMPORTANT]
> Unity 内での Application Insights を使用するには、DLL を Newtonsoft DLL と共にインポートする必要があります。 インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。 バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。

独自のプロジェクトに Application Insights をインポートするには、必ず確保[ダウンロード、'.unitypackage'、プラグインを含む](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)します。 次に、次の操作を行います。

1.  追加、 **.unitypackage**に Unity を使用して、**資産\>パッケージのインポート\>カスタム パッケージ**メニュー オプション。

2.  **Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-22.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、 **Insights**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:

    -   Microsoft.ApplicationInsights

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-23.png)

5.  この*プラグイン*ように選択すると、 **Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、 をクリックし、**適用**します。 これは、ファイルが正しく構成されていることを確認するだけです。

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > このようなプラグインをマークするには、Unity エディターでのみ使用することを構成します。 Dll プロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内のさまざまなセットがあります。

6.  次を開く必要があります、 **WSA**フォルダー内で、 **Insights**フォルダー。 構成した同じファイルのコピーが表示されます。 このファイルを選択し、インスペクターのことを確認します**Any プラットフォーム**は**unchecked**、ことを確認します**のみ** **WSAPlayer** は、**チェック**します。 **[適用]** をクリックします。

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-25.png)

7. 次のようになりましたが必要**手順 4 ~ 6**が、 *Newtonsoft*プラグイン代わりにします。 参照してください、次のスクリーン ショットのように、結果がなります。

    ![Unity パッケージをインポートします。](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>第 4 章 - を設定すると、カメラとユーザー コントロール

この章では、ユーザーを表示し、シーン内を移動できるように、カメラとコントロールを設定します。

1.  階層 パネルで、空の領域で右クリックして**作成** > **空**します。

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-26.png)

2.  新しい空の GameObject に名前を変更**カメラ親**します。

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-27.png)

3.  [階層] パネルで空の領域で右クリックし**3D オブジェクト**、次に**球**します。

4.  球体の名前を変更**右側**します。

5.  設定、**スケールを変換**を右側の**0.1、0.1、0.1**

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-28.png)

6.  削除、**球 Collider**コンポーネント をクリックして右側から、**歯車**で、*球 Collider*コンポーネント、し**コンポーネントの削除**.

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-29.png)

7.  階層パネル ドラッグで、 **Main Camera**と**右側**オブジェクトを**カメラ親**オブジェクト。

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-30.png)

8.  設定、**変換位置**両方の**Main Camera**と**右側**オブジェクトを**0, 0, 0**します。

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-31.png)

    ![カメラとユーザー コントロールを設定します。](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>第 5 章 - Unity シーン内のオブジェクトを設定

ここでは、ユーザーが操作できる、シーンのいくつかの基本的な図形を作成します。

1.  空の領域で右クリックし、*階層パネル*、次に**3D オブジェクト**を選択し、**平面**します。

2.  平面を設定**位置を変換**に**0、-1、0**します。

3.  平面を設定**スケールを変換**に**5, 1, 5**します。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-33.png)

4.  使用する基本的な素材を作成、**平面**オブジェクト、その他の図形がわかりやすくなるようにします。 移動、*プロジェクト パネル*、右クリックし、**作成**、その後に**フォルダー**、新しいフォルダーを作成します。 名前を付けます**資料**します。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-34.png) ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-35.png)

5.  開く、**資料**フォルダー、し、右クリックし、 をクリックします**作成**、し**マテリアル**、新しい素材を作成します。 名前を付けます**青い**します。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-36.png) ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-37.png)

6.  新しい**青**素材を選択すると、参照で、*インスペクター*、と共に四角形のウィンドウをクリックします。 **Albedo**します。 青の色を選択します (次の 1 つの図は、 **16 進数の色。\#3592FFFF**)。 選択した後は、閉じるボタンをクリックします。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-38.png)

7.  新しいマテリアルをドラッグして、**資料**フォルダー、新たに作成した**平面**、シーン内で (またはの上にドロップ、**平面**オブジェクト内、 *階層*)。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-39.png)

8.  空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、Capsule**します。

    -  **Capsule**変更選択すると、その**変換***位置*を: **-10, 1, 0**します。

9.  空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、Cube**します。

    -  **キューブ**変更選択すると、その**変換***位置*に。**0, 0, 10**.

10. 空の領域で右クリックし、*階層パネル*、次に**3 D オブジェクト、球体**します。

    -  **球**変更選択すると、その**変換***位置*に。**10, 0, 0**.

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > これら*位置*値は*提案*します。 自由にカメラから遠すぎてオブジェクト間の距離がない場合は、アプリケーションのユーザーを簡単に好きなに、オブジェクトの位置を設定できます。

11. アプリケーションが実行されている場合、これを実現するために、シーン内のオブジェクトを識別するためにできるようにする必要がある、タグ付けする必要があります。 選択して、オブジェクトの 1 つ、*インスペクター*パネルで、をクリックして**タグを追加しています.** 、スワップされますが、*インスペクター*で、**タグし、レイヤー**パネル。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. をクリックして、 **+ (正符号 +)** 記号、としてタグの名前を入力**ObjectInScene**します。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 別の名前、タグを使用する場合もこの変更が行われたことを確認する必要があります、 *DataFromAnalytics*、 *ObjectTrigger*、と*視線*、後で、スクリプトを、。オブジェクトが検出され、検出されると、シーン内で。

13. 作成したタグを 3 つのオブジェクトのすべてに適用する必要があります。 *階層*、保持、 **Shift**キーをクリック、 **Capsule**、**キューブ**、および**球**、オブジェクトは、次に、*インスペクター*、と共にドロップダウン メニューをクリックします。**タグ**、順にクリックします、 *ObjectInScene*タグを作成します。

    ![Unity シーン内のオブジェクトを設定します。](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>第 6 章 - ApplicationInsightsTracker クラスを作成します。

最初のスクリプトを作成する必要があるは**ApplicationInsightsTracker**は責任を負います。

1.  Azure Application Insights に送信するためのユーザー操作に基づいてイベントを作成します。

2. ユーザーの操作に応じて、適切なイベント名を作成します。

3. Application Insights サービスのインスタンスにイベントを送信しています。

このクラスを作成します。

1.  右クリックし、*プロジェクト パネル*、し**作成** > **フォルダー**します。 フォルダーの名前**スクリプト**します。

    ![ApplicationInsightsTracker クラスを作成します。](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker クラスを作成します。](images/AzureLabs-Lab309-47.png)

2.  **スクリプト**フォルダーが作成されると、ダブルクリックして、開きます。 その後、そのフォルダー内で右クリックし、**作成** >   **C#スクリプト**します。 スクリプトの名前**ApplicationInsightsTracker**します。

3.  ダブルクリックして、新しい**ApplicationInsightsTracker**スクリプト ファイルを開く**Visual Studio**します。

4.  更新するスクリプトの上部にある名前空間以下のとおり。

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  クラス内には、次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > 設定、 **instrumentationKey、applicationId および API_Key**を使用して、適切な値、*サービス キー*で説明したように、Azure Portal から[第 1 章](#chapter-1---the-azure-portal)手順 9以降。

6.  追加し、 **Start()** と**Awake()** メソッドで、クラスを初期化するときに呼び出されます。

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  イベントと、アプリケーションで登録されているメトリックの送信を行うメソッドを追加します。

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-7---create-the-gaze-script"></a>Chapter 7 - 視線入力スクリプトを作成します。

次のスクリプトを作成するには、**視線**スクリプト。 このスクリプトは作成を担当する、 *Raycast*からフォワード投影は、 *Main Camera*ユーザーが見るオブジェクトを検出します。 ここで、 *Raycast*を持つオブジェクトで、ユーザーが探している場合を識別する必要があります、 **ObjectInScene** 、タグを付けるし、ユーザーはどのくらいの時間をカウントし、 *gazes*でそのオブジェクト。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**視線**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。

4.  次のように、既存のコードに置き換えます。

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  内で、**視線**クラスで、次のコードを追加、 **Update()** プロジェクトにメソッドを*Raycast*ターゲット ヒットの検出と。

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  追加、 **ResetFocusedObject()** メソッドは、データを送信する**Application Insights**オブジェクトで、ユーザーが検索する場合。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  完了したので、**視線**スクリプト。 変更を保存*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-8---create-the-objecttrigger-class"></a>8 - 章 ObjectTrigger クラスを作成します。

次のスクリプトを作成する必要があるは**ObjectTrigger**は責任を負います。

- メイン カメラの衝突の必要なコンポーネントを追加します。
- カメラが近くとしてタグ付けされたオブジェクトがかどうかを検出する**ObjectInScene**します。

スクリプトを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**ObjectTrigger**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。 次のように、既存のコードに置き換えます。

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>9 - 章 DataFromAnalytics クラスを作成します。

作成する必要がありますこれで、 **DataFromAnalytics**を担当するスクリプト。

- どのオブジェクトがされてに近づくと、カメラで最も analytics データをフェッチしています。
- 使用して、*サービス キー*、Azure Application Insights のサービス インスタンスと通信できるようにします。
- シーン内のオブジェクトを並べ替え、これに基づいてが最上位のイベント数。
- 最も approached のオブジェクトのマテリアルの色を変更する*緑色*します。

スクリプトを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**DataFromAnalytics**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。

4.  次の名前空間を挿入します。

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  スクリプト内で、次のように挿入します。

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  内で、 **DataFromAnalytics**クラス、直後、 **Start()** メソッドと呼ばれる次のメソッドを追加**FetchAnalytics()** します。 このメソッドは、キー値のペアのリストに追加、 *GameObject*とプレース ホルダーのイベントのカウント数。 初期化し、 **GetWebRequest()** コルーチンします。 クエリ構造への呼び出しの*Application Insights*このメソッド内で見つかんだことができますも、として、*クエリ URL*エンドポイント。

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  すぐ下、 **FetchAnalytics()** メソッドというメソッドを追加**GetWebRequest()** 、返された、 *IEnumerator*します。 このメソッドは、特定の対応するイベントを発生回数の合計を要求する責任を負います*GameObject*が内で呼び出された*Application Insights*します。 送信されたすべてのクエリが返されるときに、 **DetermineWinner()** メソッドが呼び出されます。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  次の方法は**DetermineWinner()** の一覧の並べ替え*GameObject*と*Int*最大イベント数に従ってのペア。 マテリアルの色を変更し、 *GameObject*に*緑色*(フィードバックの最大数を持つ) として。 これには、分析結果を含むメッセージが表示されます。

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  受け取った JSON オブジェクトを逆シリアル化するために使用するクラスの構造を追加*Application Insights*します。 一番下にこれらのクラスを追加、 **DataFromAnalytics**クラス ファイル、**外**クラス定義の。

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. 変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-10---create-the-movement-class"></a>章 10 - 移動クラスを作成します。

**移動**スクリプトは、次のスクリプトを作成する必要があります。 担当します。

- カメラの方向に応じて、メイン カメラの移動は、方向に求めています。
- シーンのオブジェクトには、その他のすべてのスクリプトを追加します。

スクリプトを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**移動**します。

3.  ファイルを開くスクリプトをダブルクリックして*Visual Studio*します。

4.  次のように、既存のコードに置き換えます。

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  内で、**移動**クラス、*下*空**Update()** メソッド、手の形のコント ローラーを使用して仮想空間に移動するユーザーを許可する次のメソッドを挿入します。

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  最後に、メソッドの呼び出し内の追加、 **Update()** メソッド。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-11---setting-up-the-scripts-references"></a>第 11 章 – スクリプト参照の設定

この章では、配置する必要があります、**移動**にスクリプト、**カメラ親**し、その参照のターゲットを設定します。 他のスクリプトに必要な場所に配置するスクリプトを処理し、します。

1.  **スクリプト**フォルダーで、*プロジェクト パネル*、ドラッグ、**移動**スクリプトを**カメラ親**内にあるオブジェクトは、*階層パネル*します。

    ![Unity シーン内のスクリプト参照の設定](images/AzureLabs-Lab309-48.png)

2.  をクリックして、**カメラ親**します。 *階層パネル*、ドラッグ、**右側**オブジェクトから、*階層パネル*、参照先を**コント ローラー**で、*インスペクター パネル*します。 設定、**ユーザー速度**に**5**、次の図に示すようにします。

    ![Unity シーン内のスクリプト参照の設定](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第 12 章 - Unity プロジェクトをビルド

このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します**ビルド設定**、(**ファイル** > **ビルド設定**)。

2.  **Build Settings**ウィンドウで、をクリックして**ビルド**します。

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-50.png)

3.  A**ファイル エクスプ ローラー**ウィンドウがポップアップで、ビルドの場所の入力を求めます。 新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-51.png)

    1.  開く、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**MR\_Azure\_アプリケーション\_Insights**します。

        ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-52.png)

    2.  **MR\_Azure\_アプリケーション\_Insights**フォルダーを選択すると、クリックして**フォルダーの選択**します。 プロジェクトは、ビルドを 1 分程度かかります。

4.  次の*ビルド*、**ファイル エクスプ ローラー**新しいプロジェクトの場所が示されますが表示されます。

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>第 13 章 - MR_Azure_Application_Insights アプリ、マシンをデプロイします。

展開する、 **MR\_Azure\_アプリケーション\_Insights**ローカル コンピューター上のアプリ。

1.  ソリューション ファイルを開き、 **MR\_Azure\_アプリケーション\_Insights**でアプリ**Visual Studio**します。

2.  **ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。

3.  **ソリューション構成**選択**デバッグ**します。

    ![UWP のソリューションに Unity プロジェクトをビルドします。](images/AzureLabs-Lab309-53.png)

4.  移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。

5.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。

6. 複合現実のアプリケーションを起動します。

7. オブジェクトに近づいていると、それを見て、シーンの移動時に、 *Azure Insight サービス*十分なイベント データが収集が緑に最も対処されているオブジェクトが設定されます。

> [!IMPORTANT] 
> 平均待機時間を中に、*イベントとメトリック*約 15 分は、サービスによって収集されるように、いくつかの状況で最大 1 時間がかかる場合があります。

## <a name="chapter-14---the-application-insights-service-portal"></a>第 14 章 – Application Insights サービス ポータル

シーンを中心にローミングしたし、いくつかのオブジェクトで gazed で収集されたデータを表示できます、 *Application Insights サービス*ポータル。

1.  Application Insights サービス ポータルに戻ります。

2.  をクリックして*メトリックス エクスプ ローラー*します。

    ![収集されたデータを見る](images/AzureLabs-Lab309-54.png)

3.  表すグラフを含むタブが開きます、*イベントとメトリック*アプリケーションに関連します。 前述のように、グラフに表示されるデータ (最大 1 時間) まで時間がかかる場合があります。

    ![収集されたデータを見る](images/AzureLabs-Lab309-55.png)

4.  をクリックして、*イベント バー*で、*イベントの合計*でその名前を持つイベントの詳細な内訳を表示する、アプリケーションのバージョン。

    ![収集されたデータを見る](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Application Insights サービス アプリケーションの終了

これで、アプリ内のユーザーのアクティビティを監視する Application Insights サービスを利用している mixed reality アプリを構築します。

![コースの結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

**手順 1**

手動で作成する, ObjectInScene オブジェクトを起動し、スクリプト内で平面上の座標を設定します。 これにより、質問を入力できます Azure どのような最も人気のあるオブジェクトが (視線の先または近接検索の結果からいずれか) と生成、*余分な*それらのオブジェクトのいずれか。

**手順 2**

最も重要なデータを取得して、アプリケーションで時間その機微なデータを実装するように、時間で Application Insights 結果を並べ替えます。

