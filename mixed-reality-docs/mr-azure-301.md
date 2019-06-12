---
title: MR および Azure 301 - 言語の翻訳
description: このコースでは、複合現実のアプリケーション内で Azure Translator Text API を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、translator のテキスト、没入型、hololens、vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603610"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR と Azure 301:言語翻訳

このコースでは、Translator Text API、Azure Cognitive Services を使用して、複合現実アプリケーションに翻訳機能を追加する方法を学びます。

![最終的な製品](images/AzureLabs-Lab1-00.png)

Translator Text API は、翻訳のほぼリアルタイムで機能するサービスです。 サービスはクラウド ベースであり、REST API 呼び出しを使用して、アプリが行うことができますを別の言語のテキストを翻訳するニューラル機械翻訳テクノロジを使用します。 詳細については、次を参照してください。、 [Translator Text API の Azure ページ](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)します。

このコースを修了、以下を実行できる必要が複合現実のアプリケーションが用意されます。

1.  ユーザーは、没入型の (VR) ヘッドセットに接続されているマイク (または、HoloLens の内蔵マイク) に向かって話します。
2.  アプリは、ディクテーションをキャプチャし、Azure の Translator Text API に送信します。
3.  Unity シーン内の単純な UI グループで、変換結果が表示されます。

このコースでは、Unity に基づくサンプル アプリケーションに Translator サービスから結果を取得する方法を説明します。 最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 301:言語翻訳</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。 コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。 HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- (ヘッドセットには、組み込みのマイクとスピーカーを持っていない) 場合は、内蔵マイクでヘッドフォン
- Azure のセットアップや変換の取得のためのインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

- このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
- このチュートリアルのコードは、PC に接続されている既定のマイク デバイスから記録できます。 既定のマイク デバイスが音声のキャプチャに使用する予定のデバイスに設定されていることを確認します。
- ディクテーションを有効にする PC を許可するには**設定 > プライバシーに関する > 読み上げ、手描き入力機能 (&) を入力する** ボタンを選択**音声サービスをオンにして、入力候補**します。
- マイク、ヘッドホンを接続されている (またはに組み込まれて) を使用している場合、ヘッドセット、オプションの確認で「マイ ヘッドセットを着用するときに切り替えるヘッドセット マイク」がオン**設定 > 複合現実 > オーディオおよび音声**。

   ![複合現実の設定](images/AzureLabs-Lab1-00-5.png)

   ![マイクの設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> このラボのイマーシブ ヘッドセットを開発している場合は、オーディオ出力デバイスの問題を発生する可能性がありますに注意します。 これは、Unity、以降のバージョンの Unity (Unity 2018.2) での問題が原因です。 この問題は、Unity が実行時に既定のオーディオ出力デバイスを変更することを防ぎます。 回避策としては、上記の手順を完了したことを確認して閉じて再エディターを開き、この問題がそれ自体を提示します。

## <a name="chapter-1--the-azure-portal"></a>第 1 章 – Azure Portal

Azure Translator API を使用するには、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  ログイン、 [Azure Portal](https://portal.azure.com)します。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**上で左上隅にある"Translator Text API です"を検索。 選択**入力**します。

    ![新しいリソース](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

3.  新しいページがの説明を入力、 *Translator Text API*サービス。 このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。

    ![Translator Text API サービスを作成します。](images/AzureLabs-Lab1-03.png)

4.  クリックすると**作成**:

    1. 必要な挿入**名前**このサービス インスタンス。
    2. 適切な選択**サブスクリプション**します。
    3. 選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Translator のテキスト サービス*、(F0 という名前)、free レベルを使用することがあります。
    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. 確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。
    6. また、このサービスに適用される条件を理解したことを確認する必要があります。
    7. **[作成]** を選択します。

        ![[作成] ボタンを選択します。](images/AzureLabs-Lab1-04.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。
6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。 

    ![Azure サービスの作成の通知](images/AzureLabs-Lab1-05.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。 

    ![リソースのポップアップに移動します。](images/AzureLabs-Lab1-06.png)

8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 新しい Translator Text API のサービス インスタンスが表示されます。 

    ![Translator Text API のサービス ページ](images/AzureLabs-Lab1-07.png)

9.  このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。 
10. *クイック スタート*のページ、 *Translator Text*サービスは、最初のステップに移動します*キーを取得する*、 をクリック**キー** (することできますまたこれは実現キー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。 これが明らかに、サービス*キー*します。
11. このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章 – Unity プロジェクトの設定

設定して、mixed reality イマーシブ ヘッドセットをテストします。

> [!NOTE]
> アニメーション コント ローラーは、このコースの必要はありません。 イマーシブ ヘッドセットの設定をサポートする場合は、次のようにしてください。[次の手順に従って](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。

次が複合現実での開発の一般的な設定と、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab1-08.png)

2.  これで、Unity プロジェクト名を指定する必要があります。 挿入**MR_Translation**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab1-09.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab1-10.png)

4.  次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab1-11.png)

5.  移動して**ファイル > Build Settings**ことを確認してください。

    1. **デバイスを対象に**に設定されている**任意のデバイス**します。

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2. **ビルドの種類**に設定されている**D3D**
    3. **SDK**に設定されている**インストールされている最新**
    4. **Visual Studio バージョン**に設定されている**インストールされている最新**
    5. **ビルドおよび実行**に設定されている**ローカル マシン**
    6. シーンを保存し、ビルドに追加します。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab1-12.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab1-13.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_TranslationScene**、キーを押します**保存します**。

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab1-14.png)

            > 注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。 Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。

    7. 設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

6. *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab1-15.png)

7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1. **ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。
        2. **バックエンドの scripting**べき **.NET**
        3. **API の互換性レベル**べき **.NET 4.6**

            ![その他の設定を更新します。](images/AzureLabs-Lab1-16.png)
      
    2. 内で、**発行の設定**] タブの [**機能**、確認してください。

        1. **InternetClient**
        2. **マイク**

            ![発行の設定を更新しています。](images/AzureLabs-Lab1-17.png)

    3. パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![X の R の設定を更新します。](images/AzureLabs-Lab1-18.png)

8.  戻り**Build Settings**、 *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。 
9.  ビルド設定ウィンドウを閉じます。
10. シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 – メイン カメラのセットアップ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*のこのコンポーネントである、コース、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)、としてプロジェクトにインポート、 [ *カスタム パッケージ*](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-results-class)します。 Unity プロジェクトを作成する必要があります。

1.  *階層パネル*、という名前のオブジェクトが表示されます**Main Camera**、「内部」アプリケーションが表示されたら、このオブジェクトは、"head"の観点を表します。
2.  選択する前にある Unity ダッシュ ボードで、**メイン カメラの GameObject**します。 表示になります、*インスペクター パネル*(一般にダッシュ ボードで、右側にあります) をさまざまなコンポーネントが表示されます*GameObject*で*変換*後に、上部にある*カメラ*、およびその他のコンポーネント。 これが正しく配置されているため、メイン カメラの変換をリセットする必要があります。
3.  これを行うには、選択、**歯車**カメラの横にあるアイコン*変換*コンポーネント、および選択**リセット**します。 

    ![メイン カメラの変換をリセットします。](images/AzureLabs-Lab1-19.png)
 
4.  *変換*し、コンポーネントのようになります。

    1. *位置*に設定されている**0, 0, 0**
    2. *回転*に設定されている**0, 0, 0**
    3. *スケール*に設定されている**1, 1, 1**

        ![カメラの情報を変換します。](images/AzureLabs-Lab1-20.png)

5.  [次へ]、 **Main Camera**選択したオブジェクトを参照してください、**コンポーネントの追加**の一番下にあるボタン、*インスペクター パネル*します。 
6.  そのボタンを選択し、検索 (入力するか*オーディオ ソース*検索フィールドまたはセクションでは、移動に) と呼ばれるコンポーネントの**オーディオ ソース**次に示すようを選択します (enter キーを押しに機能します)。
7.  *オーディオ ソース*コンポーネントに追加されます、 **Main Camera**、次のようにします。

    ![オーディオ ソース コンポーネントを追加します。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Microsoft HoloLens のも、次を変更する必要がありますに含まれています、**カメラ**コンポーネントを**Main Camera**:
    > - **フラグをオフにします。** 純色です。
    > - **バック グラウンド**' 黒、アルファ 0' – 16 進カラー: #00000000 します。

## <a name="chapter-4--setup-debug-canvas"></a>第 4 章 – セットアップ デバッグ キャンバス

入力と変換の出力を表示するには、基本的な UI を作成する必要があります。 このコースでは、いくつかの 'Text' オブジェクト データを表示すると、キャンバスの UI オブジェクトを作成します。

1.  空の領域で右クリックし、*階層パネル* **UI**、追加、**キャンバス**します。

    ![新しいキャンバス UI オブジェクトを追加します。](images/AzureLabs-Lab1-22.png)

2.  選択したら、キャンバス オブジェクトに、*インスペクター パネル*(コンポーネント内で、「キャンバス」)、次のように変更します。**レンダリング モード**に**ワールド空間**します。 
3.  次のパラメーターを次に、変更、*インスペクター パネルの Rect 変換*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *幅*500 -
    3. *高さ*300 -
    4. *スケール* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![キャンバスの四角形の変換を更新します。](images/AzureLabs-Lab1-23.png)
 
4.  右クリックして、**キャンバス**で、*階層パネル* **UI**、追加、**パネル**。 これは、**パネル**シーンに表示されるテキストの背景を提供します。
5.  右クリックして、**パネル**で、*階層パネル* **UI**、追加、**テキスト オブジェクト**。 合計で 4 つの UI テキスト オブジェクトを作成するまで、同じプロセスを繰り返します (ヒント: 押すだけ選択されている最初の 'Text' オブジェクトがあれば、 **Ctrl + が '** 合計で 4 つの操作をした後、複製する)。 
6.  各**テキスト オブジェクト**をことを選択して、次の表で、パラメーターを設定する、*インスペクター パネル*。

    1. *Rect 変換*コンポーネント。

        | 名前                   | 変換 -*位置*             | 幅      | 高さ    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. **テキスト (スクリプト)** コンポーネント。


        | 名前                   | Text               | フォント サイズ    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | マイクの状態: | 20           |
        | AzureResponseLabel     | Azure の Web 応答 | 20           |
        | DictationLabel         |   言っただけです。   | 20           |
        | TranslationResultLabel |    変換:    | 20           |

        ![UI のラベルの対応する値を入力します。](images/AzureLabs-Lab1-24.png)

    3. また、フォント スタイルをください**太字**します。 これは、テキストを読みやすきます。

        ![太字のフォント。](images/AzureLabs-Lab1-25.png)

7.  各*UI テキスト オブジェクト*で作成した[第 5 章](#chapter-5--create-the-results-class)を新規作成*子* **UI テキスト オブジェクト**します。 これらの子は、アプリケーションの出力に表示されます。 作成*子*、目的の親を右クリックしてからオブジェクト (例: *MicrophoneStatusLabel*) し、 **UI**し、**テキスト**.
8.  これらの子のそれぞれについて、選択して、使用して、次の表は、[Inspector] パネルでのパラメーターを設定します。

    1. **Rect 変換**コンポーネント。

        | 名前                  | 変換 -*位置* | 幅      | 高さ    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | 0 の Y-30 Z 0 X          | 300        | 30        |
        | AzureResponseText     | 0 の Y-30 Z 0 X          | 300        | 30        |
        | DictationText         | 0 の Y-30 Z 0 X          | 300        | 30        |
        | TranslationResultText | 0 の Y-30 Z 0 X          | 300        | 30        |

    2. **テキスト (スクリプト)** コンポーネント。

        | 名前                  | Text          | フォント サイズ    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 次に、テキストの各コンポーネントの 'centre' の配置オプションを選択します。

    ![テキストを配置します。](images/AzureLabs-Lab1-26.png)

10. 確認する、**子 UI テキスト**オブジェクトが読みやすく、変更、*色*します。 これには (現在は ' 黒') の横に、バーをクリックすると、*色*します。 

    ![対応する UI テキスト出力用の値を入力します。](images/AzureLabs-Lab1-27.png)
 
11. 次に、新しい、少し、*色*ウィンドウで、変更、 *16 進カラー*に。**0032EAFF**

    ![色を青を更新します。](images/AzureLabs-Lab1-28.png)
 
12. 以下は、方法、 **UI**になります。
    1.  *階層パネル*:

        ![指定された構造内の階層があります。](images/AzureLabs-Lab1-29.png)

    2.  *シーン*と*ゲーム ビュー*:

        ![同じ構造でシーンやゲームのビューがあります。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第 5 章 – 結果のクラスを作成します。

最初のスクリプトを作成する必要がありますが、*結果*クラスは、変換の結果を表示する方法を提供する責任を負います。 クラスを格納し、次が表示されます。 

- Azure からの応答の結果。
- マイクの状態です。 
- ディクテーション モード (音声テキストを) の結果。
- 変換の結果。

このクラスを作成します。 

1.  右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。 フォルダーの名前**スクリプト**します。 
 
    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab1-31.png)

    ![スクリプト フォルダーを開きます。](images/AzureLabs-Lab1-32.png)
 
2.  **スクリプト**フォルダーの作成、アイコンをダブルクリックして開きます。 そのフォルダーを右クリックし、内**作成 >** し**C#スクリプト**します。 スクリプトの名前*結果*します。 

    ![最初のスクリプトを作成します。](images/AzureLabs-Lab1-33.png)
 
3.  新しいをダブルクリックします。*結果*スクリプト ファイルを開く**Visual Studio**します。
4.  次の名前空間を挿入します。

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  クラス内には、次の変数を挿入します。

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  追加し、 *Awake()* メソッドで、クラスを初期化するときに呼び出されます。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最後に、UI にさまざまな結果の情報を出力することを担当するメソッドを追加します。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第 6 章 – 作成、 *MicrophoneManager*クラス

2 番目のクラスを作成するには、 *MicrophoneManager*します。

このクラスは、責任を負います。

- ヘッドセットまたは (方は、既定値) のマシンにアタッチされた録音デバイスを検出します。
- 音声 (音声) を使用すると、キャプチャし、ディクテーションを使用して、文字列として保存します。
- 音声が一時停止すると、Translator クラスにディクテーションを送信します。
- 必要な場合は、音声でキャプチャを停止するメソッドをホストします。

このクラスを作成します。 
1.  ダブルクリック、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前*MicrophoneManager*します。 
3.  Visual Studio で開くことに新しいスクリプトをダブルクリックします。
4.  上部にある、次と同じである名前空間の更新、 *MicrophoneManager*クラス。

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  次に、内部では、次の変数を追加、 *MicrophoneManager*クラス。

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。 これらが、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  できます*削除*、 *Update()* メソッドのため、このクラスは使用されません。
8.  メソッドに渡すの開始し、音声のキャプチャを停止する、アプリが使用する必要があります、 *Translator*クラスと、すぐにビルドします。 次のコードをコピーして貼り付ける下に、 *Start()* メソッド。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > このアプリケーションのことはありませんが、使用、 *StopCapturingAudio()* メソッドも用意されていますここでは、アプリケーションでのオーディオのキャプチャを停止する機能を実装する必要があります。

9.  音声が停止したときに呼び出されるディクテーション ハンドラーを追加する必要があります。 このメソッドは、ディクテーションされたテキストに合格し、 *Translator*クラス。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Visual Studio で Unity に戻る前に変更を保存することを確認します。

> [!WARNING]  
> この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール*パネル (「名前 'トランスレーター' が存在しません...」)。 これは、コードを参照しているため、 *Translator*クラスで、[次へ] の章で作成されます。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第 7 章 – Azure と translator サービスへの呼び出し

最後のスクリプトを作成する必要がありますが、 *Translator*クラス。 

このクラスは、責任を負います。

-   使用してアプリを認証*Azure*、exchange の**Auth トークン**します。
-   使用して、 **Auth トークン**テキストを送信する (から受信した、 *MicrophoneManager*クラス) を変換します。
-   変換された結果を受け取るに渡すと、*結果*UI で視覚化対象であるクラス。

このクラスを作成します。 
1.  移動して、**スクリプト**以前に作成したフォルダーです。 
2.  右クリックし、**プロジェクト パネル**、**作成 >C#スクリプト**します。 スクリプトを呼び出す*Translator*します。
3.  新しいをダブルクリックします。 *Translator*開くスクリプト**Visual Studio を使用した**します。
4.  ファイルの先頭には、次の名前空間を追加します。

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  内で、次の変数を追加し、 *Translator*クラス。

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 言語に挿入された言語**enum**は単なる例です。 場合; を追加してみてください。[API は、60 を超える言語をサポートしている](https://docs.microsoft.com/azure/cognitive-services/translator/languages)(クリンゴンを含む)。
    > - [より対話的なページが使用可能な言語をカバーする](https://www.microsoft.com/translator/business/languages/)ページに設定されているサイトの言語にあるときにのみ表示されますが注意 'en-' (および、Microsoft のサイトがネイティブ言語へのリダイレクトを可能性があります)。 または、URL を変更することにより、ページの下部にあるサイトの言語を変更できます。
    > - **AuthorizationKey**上のコード スニペット内の値である必要があります、**キー**を申し込んだときに受信した、 *Azure Translator Text API*します。 これで説明した[第 1 章](#chapter-1--the-azure-portal)します。

6.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。 
7.  ここでは、コードが呼び出しを行うは*Azure*承認キーを使用して、*トークン*。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > トークンは、10 分後に切れます。 によっては、アプリのシナリオでは、複数回呼び出して同じコルーチンを作成する必要があります。

8.  トークンを取得するコルーチン次に示します。

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > IEnumerator メソッドの名前を編集する場合**GetTokenCoroutine()** 、更新する必要がある、 *StartCoroutine*と*StopCoroutine*上記のコードで文字列値を呼び出します。 [Unity のドキュメントに従って](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)特定を停止するには、*コルーチン*文字列値メソッドを使用する必要があります。

9.  次に、受信したテキストの翻訳を取得する (その下「サポート」ストリーム メソッド) を使用して、コルーチンを追加、 *MicrophoneManager*クラス。 このコードに送信するクエリ文字列の作成、 *Azure Translator Text API*、し、内部の Unity UnityWebRequest クラスを使用して、クエリ文字列のあるエンドポイントに 'Get' 呼び出しを行います。 結果は、結果オブジェクトの翻訳を設定するのには使用されます。 次のコードは、実装を示しています。

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-8--configure-the-unity-scene"></a>章 – 8 Unity シーンを構成します。

1.  戻る Unity エディターで、をクリックし、ドラッグ、 *結果* クラス *から* 、 **スクリプト** フォルダーを **Main Camera** 内のオブジェクト *階層パネル* します。
2.  をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。 内で、新しく追加した表示になります*スクリプト*コンポーネントでは、空の値の 4 つのフィールドがあります。 これらは、コード内のプロパティに出力参照です。 
3.  適切なドラッグ**テキスト**オブジェクトから、*階層パネル*これら 4 つのスロット、次の図に示すようにします。

    ![指定した値を持つターゲットの参照を更新します。](images/AzureLabs-Lab1-34.png)
  
4.  次に、をクリックし、ドラッグ、 *Translator*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*します。 
5.  次に、をクリックし、ドラッグ、 *MicrophoneManager*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*。 
6.  最後に、をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。 上にドラッグした先のスクリプトである 2 つのドロップ ダウン ボックスは、言語を設定することがわかります。
 
    ![目的の翻訳の言語の入力を確認します。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第 9 章 – 複合現実でのテスト

この時点で、シーンが正しく実装されていることをテストする必要があります。

次のことを確認してください。

- 説明されているすべての設定[第 1 章](#chapter-1--the-azure-portal)が正しく設定されています。 
- *結果*、 *Translator*、および*MicrophoneManager*に関連付けられているスクリプト、 **Main Camera**オブジェクト。 
- 配置した、 *Azure Translator Text API*サービス**キー**内、 **authorizationKey**変数内で、 *Translator*スクリプトです。  
- 内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。
- シーンを実行するときに、マイクの動作 (そうでない場合は、接続されているマイクことを確認、*既定*デバイス、およびある[Windows 内正しく設定して](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。

イマーシブ ヘッドセットをテストするにはキーを押して、**再生**ボタン、 *Unity エディター*します。
アプリは、添付のイマーシブ ヘッドセットで機能している必要があります。

> [!WARNING]  
> 変更する既定のオーディオ デバイスについて、Unity コンソールで、エラーが発生した場合期待どおりにシーンが機能しない可能性があります。 これは、複合現実ポータルが設定されているヘッドセットの組み込みのマイクを扱う方法に起因します。 このエラーを参照してください、単にシーンを停止、再開し、として動作する必要がありますが必要です。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>章 – 10 ビルド UWP ソリューションおよびローカル コンピューター上のサイドロード

このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します**ビルド設定**:**ファイル > の設定を作成しています.**
2.  **Build Settings**ウィンドウで、をクリックして**ビルド**します。

    ![Unity シーンを構築します。](images/AzureLabs-Lab1-36.png)
  
3.  まだ行っていない場合、ティック**UnityC#プロジェクト**します。
4.  **[Build]** をクリックします。 Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前*アプリ*します。 使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。 
5.  Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。 
6.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-11--deploy-your-application"></a>第 11 章 – 展開アプリケーション

アプリケーションを配置します。

1.  新しい Unity ビルドに移動します (、*アプリ*フォルダー) とソリューション ファイルを開くと*Visual Studio*します。
2.  ソリューション構成の選択で**デバッグ**します。
3.  ソリューション プラットフォーム で選択**x86**、**ローカル マシン**します。 

    > Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。 ただし、次の操作も必要があります。
    > - 把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。 
    > - 確認*開発者モード*は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab1-37.png)
    
 
4.  移動して**ビルド メニュー**  をクリック**ソリューションの配置**を PC にアプリケーションをサイドローディングします。
5.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。
6.  起動するには、アプリには、マイクへのアクセスを承認することが求められます。 クリックして、**はい**ボタンをクリックします。
7.  翻訳を開始する準備ができました!

## <a name="your-finished-translation-text-api-application"></a>完成した翻訳テキスト API アプリケーション

これで、音声翻訳されたテキストに変換するには、Azure 翻訳テキスト API を利用している mixed reality アプリを構築します。

![最終的な製品です。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

できる機能を追加する音声合成をアプリに返されるテキストが話されているようにでしょうか。

### <a name="exercise-2"></a>手順 2

ユーザー自体には、アプリ内のソースと出力の言語 ('から' および 'to') を変更するので、アプリが言語を変更するたびに再構築する必要はありませんが可能にします。
