---
title: MR と Azure 311 - Microsoft Graph
description: このコースでは、Microsoft Graph を利用し、複合現実のアプリケーション内での生産性を高めるデータに接続する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、graph、没入型、hololens、vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597661"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-and-azure-311---microsoft-graph"></a>MR と Azure 311 - Microsoft Graph

このコースでは、場合、使用する方法について説明します。 *Microsoft Graph*複合現実のアプリケーション内でセキュリティで保護された認証を使用して、Microsoft アカウントにログインします。 取得し、アプリケーションのインターフェイスで、スケジュールされた会議が表示されます。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph*は多くの Microsoft のサービスにアクセスできるようにする Api のセットです。 Microsoft は、これにより、あらゆる種類の接続しているユーザー データにアクセスするアプリケーションを意味する場合のリレーションシップによって接続されているリソースのマトリックスとして Microsoft Graph をについて説明します。 詳細については、次を参照してください。、 [Microsoft Graph ページ](https://developer.microsoft.com/graph)します。

開発を見つめますな球体では、Microsoft アカウントに安全にログインするユーザーを促しますの順にタップしてユーザーを指示は、アプリの作成が含まれます。 自分のアカウントにログインすると、ユーザーは同じ日のスケジュールされた会議の一覧を表示することができます。

このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。

1.  (移動にログインし、もう一度アプリにバックアップし、アプリ外) の Microsoft アカウントにログインするユーザーに通知するオブジェクトのタップ ジェスチャを使用して、タップします。
2.  その日のスケジュールされた会議の一覧を表示します。 

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 311:Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- Azure のセットアップと Microsoft Graph データの取得のインターネット アクセス
- 有効な**Microsoft アカウント**(個人または職場/学校)
- 同じ Microsoft アカウントを使用して、いくつかの会議は現在の日のスケジュール

### <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>1 -」の章では、アプリケーション登録ポータルでアプリを作成します。

作成し、アプリケーションを登録する必要がありますはまず、**アプリケーション登録ポータル**します。

この章に通話を行うことを許可するサービスのキーも検索が*Microsoft Graph*アカウント コンテンツにアクセスします。

1.  移動し、 [Microsoft アプリケーション登録ポータル](https://apps.dev.microsoft.com)Microsoft アカウントを使用してログインします。 ログインしたら後に、リダイレクトされます、**アプリケーション登録ポータル**します。

2.  **アプリケーション**セクションで、ボタンをクリックして、**アプリの追加**します。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **アプリケーション登録ポータル**、以前に学習したかどうかに応じて異なるよう*Microsoft Graph*します。 以下のスクリーン ショットには、これらの異なるバージョンを表示します。

3.  クリックして、アプリケーションの名前を追加**作成**です。

    ![](images/AzureLabs-Lab311-03.png)

4.  アプリケーションが作成されたら、アプリケーションのメイン ページにリダイレクトされます。 コピー、**アプリケーション Id**を安全な場所にこの値をメモしておきますとは、コードですぐに使用されます。

    ![](images/AzureLabs-Lab311-04.png)

5.  **プラットフォーム**セクションで、必ず**ネイティブ アプリケーション**が表示されます。 場合*いない* をクリックして**プラットフォームの追加**選択**ネイティブ アプリケーション**します。

    ![](images/AzureLabs-Lab311-05.png)

6.  下へスクロールし、同じページで」というセクション**Microsoft Graph のアクセス許可**アプリケーションのアクセス許可を追加する必要があります。 をクリックして**追加**横に**委任されたアクセス許可**します。

    ![](images/AzureLabs-Lab311-06.png)

7.  アプリケーションへのユーザーの予定表にアクセスするためのチェックと呼ばれるボックス**Calendars.Read**  をクリック**OK**します。

    ![](images/AzureLabs-Lab311-07.png)

8.  下部までスクロールし、**保存**ボタンをクリックします。

    ![](images/AzureLabs-Lab311-08.png)

9.  保存を確認してからログアウトしたことができます、**アプリケーション登録ポータル**します。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章 - Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。

    ![](images/AzureLabs-Lab311-09.png)

2.  Unity プロジェクトの名前を指定する必要があります。 挿入**MSGraphMR**します。 必ず、プロジェクト テンプレートに設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![](images/AzureLabs-Lab311-10.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![](images/AzureLabs-Lab311-11.png)

4.  移動して**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。

    ![](images/AzureLabs-Lab311-12.png)

5.  **ファイル > Build Settings**、ことを確認します。

    1. **デバイスを対象に**に設定されている**HoloLens**
    2. **ビルドの種類**に設定されている**D3D**
    3. **SDK**に設定されている**インストールされている最新**
    4. **Visual Studio バージョン**に設定されている**インストールされている最新**
    5. **ビルドおよび実行**に設定されている**ローカル マシン**
    6. シーンを保存し、ビルドに追加します。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![](images/AzureLabs-Lab311-13.png)

        2. これと、任意の将来、シーンの新しいフォルダーを作成します。 選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![](images/AzureLabs-Lab311-14.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_ComputerVisionScene**、順にクリックします**保存**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。 Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。

    7.  設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

6.  *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![](images/AzureLabs-Lab311-16.png)

7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1.  **Scripting** **ランタイム バージョン**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。

        2. **バックエンドの scripting**べき **.NET**

        3. **API の互換性レベル**べき **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、確認**仮想現実サポート**、ことを確認します、 **Windows Mixed RealitySDK**が追加されます。

        ![](images/AzureLabs-Lab311-19.png)

8.  戻り*Build Settings*、 *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンします。

9.  閉じる、 *Build Settings*ウィンドウ。

10.  シーンとプロジェクトを保存 (**ファイル > シーンの保存/ファイル > プロジェクトの保存**)。

## <a name="chapter-3---import-libraries-in-unity"></a>第 3 章 - Unity でのインポート ライブラリ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[311.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5---create-meetingsui-class)します。

使用する*Microsoft Graph*する必要がある Unity 内での使用、 **Microsoft.Identity.Client** DLL。 (つまり、プロジェクトのビルド後の編集) Unity プロジェクトをビルドした後に NuGet パッケージを追加する必要があるただし、Microsoft Graph の SDK を使用することです。 必要な Dll を Unity に直接インポートする方が簡単と見なされます。

> [!NOTE]
> インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。 バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。

インポートする*Microsoft Graph*独自のプロジェクトに[MSGraph_LabPlugins.zip ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)します。 テスト済みのライブラリのバージョンでは、このパッケージが用意されています。

カスタム Dll を Unity プロジェクトに追加する方法を詳しく把握したい場合[こちらのリンク](https://docs.unity3d.com/Manual/UsingDLL.html)します。

パッケージをインポートします。

1.  使用して、Unity に Unity パッケージを追加、 **資産* > *パッケージのインポート* > *カスタム パッケージ** メニュー オプション。 ダウンロードしたパッケージを選択します。

2.  **Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。

    ![](images/AzureLabs-Lab311-20.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、 **MSGraph**の下のフォルダー**プラグイン**で、*プロジェクト パネル*というプラグインを選択します。 **Microsoft.Identity.Client**します。

    ![](images/AzureLabs-Lab311-21.png)

5.  *プラグイン*ように選択すると、**任意のプラットフォーム**が選択されていない、いることを確認し、 **WSAPlayer**もが選択されていないクリック**適用**. これは、ファイルが正しく構成されていることを確認するだけです。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > これらのプラグインをマークする Unity エディターでのみ使用することを構成します。 WSA フォルダーにプロジェクトがユニバーサル Windows アプリケーションとして Unity からエクスポートされた後に使用される Dll のさまざまなセットがあります。

6.  次を開く必要があります、 **WSA**フォルダー内で、 **MSGraph**フォルダー。 構成した同じファイルのコピーが表示されます。 ファイルを選択し、次に、インスペクター。

    -   いることを確認**任意のプラットフォーム**は**unchecked**、および**のみ** **WSAPlayer**は**チェック**。

    -   確認**SDK**に設定されている**UWP**、および**Scripting バックエンド**に設定されている**Dot Net**

    -   いることを確認**処理しない**は**チェック**します。

        ![](images/AzureLabs-Lab311-23.png)

7.  **[適用]** をクリックします。

## <a name="chapter-4---camera-setup"></a>第 4 章 - カメラのセットアップ

この章では、シーンのメイン カメラを設定します。

1.  *階層パネル*を選択、 **Main Camera**します。

2.  すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター*パネル。

    1.  **Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。

    2.  Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。

    3.  必ず、**変換位置**に設定されている**0, 0, 0**

    4.  設定**フラグをクリア**に**純色**

    5.  設定、**背景色**にカメラのコンポーネントの**黒、アルファ 0** **(コードを 16 進数: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  最終的なオブジェクトの構造、*階層パネル*次の図に示すようになります。

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>第 5 章「MeetingsUI クラスを作成

最初のスクリプトを作成する必要があるは**MeetingsUI**、これはホストと (ウェルカム メッセージ、手順、および会議の詳細) のアプリケーションの UI の作成を担当します。

このクラスを作成します。

1.  右クリックし、**資産**フォルダーで、*プロジェクト パネル*を選択し、**作成*> * * * フォルダー。 フォルダーの名前**スクリプト**します。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  開く、**スクリプト**フォルダー、そのフォルダー内で右クリックし、**作成*> * C\#スクリプト * *。 スクリプトの名前**MeetingsUI します。**

    ![](images/AzureLabs-Lab311-28.png)

3.  ダブルクリックして、新しい**MeetingsUI**スクリプト ファイルを開く*Visual Studio*します。

4.  次の名前空間を挿入します。

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  クラス内には、次の変数を挿入します。

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  置換し、 **Start()** メソッドを追加し、 **Awake()** メソッド。 これらが、クラスの初期化時に呼び出されます。

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  作成を担当するメソッドを追加、*会議 UI*し、要求されたときに、現在の会議を設定します。

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **削除**、 **Update()** メソッドをおよび**変更を保存**Unity に戻る前に Visual Studio で。 

## <a name="chapter-6---create-the-graph-class"></a>第 6 章 - Graph クラスを作成します。

次のスクリプトを作成するには、**グラフ**スクリプト。 このスクリプトは、ユーザーを認証し、ユーザーの予定表から現在の日付のスケジュールされた会議を取得する呼び出しを行う責任を負います。

このクラスを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**グラフ**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。

4.  次の名前空間を挿入します。

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > このスクリプトでは、コードの部分にラップされることがわかります[プリコンパイル ディレクティブ](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)、これは、Visual Studio のソリューションを構築するときに、ライブラリでの問題を回避するためにします。

5.  削除、 **Start()** と**Update()** メソッドを使用できません。

6.  外側、**グラフ**クラス、毎日のスケジュールされた会議を表す JSON オブジェクトを逆シリアル化するために必要な次のオブジェクトを挿入します。

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  内で、**グラフ**クラスで、次の変数を追加します。

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > 変更、 **appId**値を**アプリ Id**で書き留めたが**[第 1 章](#chapter-1---create-your-app-in-the-application-registration-portal)、手順 4.** します。 この値で表示される内容と同じである、**アプリケーション登録ポータルでは、** アプリケーション登録ページにします。

8.  内で、**グラフ**クラス、メソッドを追加します**SignInAsync()** と**AquireTokenAsync()** ログインの資格情報を挿入するユーザーを促します。

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  次の 2 つのメソッドを追加します。

    1.  **BuildTodayCalendarEndpoint()** 日、スケジュールされた会議を取得する期間を指定する URI を構築します。

    2.  **ListMeetingsAsync()**、要求からスケジュールされた会議*Microsoft Graph*します。

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. 完了したので、**グラフ**スクリプト。 **変更を保存**Visual studio を Unity に返す前にします。

## <a name="chapter-7---create-the-gazeinput-script"></a>Chapter 7 - GazeInput スクリプトを作成します。

作成、 **GazeInput**します。 このクラスを処理しを使用して、ユーザーの視線の先の追跡、 **Raycast**から、 **Main Camera**、前方に射影します。

スクリプトを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**GazeInput**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。

4.  追加すると共に、以下と一致する名前空間のコードを変更、'**\[System.Serializable\]**' 上記のタグ、 **GazeInput**クラスをシリアル化できるようにします。

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  内で、 **GazeInput**クラスで、次の変数を追加します。

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  追加、 **CreateCursor()** 、シーンの HoloLens のカーソルを作成しからメソッドを呼び出すメソッドを**Start()** メソッド。

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  次のメソッドは、Raycast 視線の先を有効にして、フォーカスがあるオブジェクトの追跡。

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **変更を保存**Visual studio を Unity に返す前にします。

## <a name="chapter-8---create-the-interactions-class"></a>8 -」の章の相互作用クラスを作成します。

作成する必要がありますこれで、**の相互作用**を担当するスクリプト。

-   処理、**タップ**相互作用と**カメラ視線**、「ボタン」が、シーン内のログと対話するユーザーを有効にします。

-   ユーザーと対話するため、シーン内の「ボタン」オブジェクトでログを作成します。

スクリプトを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。

2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**の相互作用**します。

3.  Visual Studio で開くことをスクリプトをダブルクリックします。

4.  次の名前空間を挿入します。

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  継承の変更、**相互作用**クラス*MonoBehaviour*に**GazeInput**します。

    ~~パブリック クラスの相互作用します。MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  内で、**相互作用**クラスは、次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  置換、**開始**メソッドは、'base' 注視クラスのメソッドを呼び出すオーバーライド メソッドであることに注意してください。 **Start()** クラスが初期化、入力の認識のための登録とサインインを作成するときに呼び出される*ボタン*シーン内。

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  追加、 **CreateSignInButton()** メソッドは、サインインをインスタンス化は*ボタン*シーン内とプロパティの設定。

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  追加、 **GestureRecognizer_Tapped()** メソッド応答、*タップ*ユーザー イベント。

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **削除**、 **Update()** メソッドし**変更を保存**Unity に戻る前に Visual Studio でします。

## <a name="chapter-9---set-up-the-script-references"></a>第 9 章 – は、スクリプト参照を設定

この章では、配置する必要があります、**の相互作用**にスクリプト、 **Main Camera**します。 他のスクリプトに必要な場所に配置するスクリプトを処理し、します。

-  **スクリプト**フォルダーで、*プロジェクト パネル*、スクリプトをドラッグして**の相互作用**を**Main Camera**オブジェクトを次に示します。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>第 10 章 – タグを設定

タグの使用、視線入力を処理するコードと、 **SignInButton**オブジェクトを識別するために、ユーザーにサインインするやり取り*Microsoft Graph*します。

タグを作成します。

1.  Unity エディターでのクリックして、 **Main Camera**で、*階層パネル*します。

2.  *インスペクター パネル* をクリックして、 **MainCamera** *タグ*をドロップダウン リストを開きます。 をクリックして**タグを追加しています.**

    ![](images/AzureLabs-Lab311-30.png)

3.  をクリックして、 **+** ボタンをクリックします。

    ![](images/AzureLabs-Lab311-31.png)

4.  タグの名前を書き込み**SignInButton** [保存] をクリックします。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第 11 章 - UWP を Unity プロジェクトをビルド

このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します*ビルド設定*(**ファイル*> * 設定 * * を作成) します。

    ![](images/AzureLabs-Lab311-33.png)

2.  まだ行っていない場合、ティック**Unity C\#プロジェクト**します。

3.  **[Build]** をクリックします。 Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前**アプリ**します。 使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。

4.  Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。

5.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-12---deploy-to-hololens"></a>HoloLens に 12 -」の章をデプロイします。

HoloLens の展開。

1.  必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード。** これには、次の手順を実行します。

    1.  ソックスを着けずに、HoloLens 中を開く、**設定**します。

    2.  移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**

    3.  注、 **IPv4**アドレス。

    4.  次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**

    5.  設定**で開発者モード**します。

2.  新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。

3.  **ソリューション構成**選択**デバッグ**します。

4.  **ソリューション プラットフォーム**、 **x86、リモート コンピューター**します。 挿入を求め、 **IP アドレス**のリモート デバイス (、HoloLens、ここでは、メモしたもの)。

    ![](images/AzureLabs-Lab311-34.png)

5.  移動して**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。

6.  アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens アプリケーション

これで、読み取り、ユーザーの予定表データの表示、Microsoft Graph を利用している mixed reality アプリを構築します。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

Microsoft Graph を使用して、ユーザーに関するその他の情報を表示するには

-   ユーザーの電子メール プロファイルの画像/電話番号

### <a name="exercise-1"></a>手順 1

Microsoft Graph の UI を移動する音声コントロールを実装します。
