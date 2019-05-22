---
title: MR と Azure 313 - IoT Hub サービス
description: Ubuntu 16.4 を実行する仮想マシンを Azure IoT Hub サービスを実装する方法については、このコースを完了し、Microsoft HoloLens または没入型の (VR) ヘッドセットを使用してメッセージ データを視覚化します。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure、mixed reality、academy、edge、iot edge、チュートリアル、api、通知、関数、テーブル、没入型、hololens、vr、iot、仮想マシン、ubuntu、python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597571"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-and-azure-313-iot-hub-service"></a>MR と Azure 313:IoT Hub サービス

![コースの結果](images/AzureLabs-Lab313-00.png)

このコースでは、実装する方法について説明します、 **Azure IoT Hub Service**仮想マシン上には、Ubuntu 16.4 オペレーティング システムを実行します。 **Azure Function App** 、Ubuntu VM から送信されるメッセージを使用して、内で結果を格納する**Azure Table Service**します。 使用してこのデータを表示できるが、 **Power BI** Microsoft HoloLens または没入型の (VR) ヘッドセット。

このコースの内容*適用*IoT Edge デバイスにこのコースでは、目的が、フォーカスがあり、仮想マシン環境でされる物理的なエッジ デバイスへのアクセスが必要ではありません。

このコースを完了するを学習します。

- デプロイを**IoT Edge モジュール**IoT デバイスを表す仮想マシン (Ubuntu 16 OS) にします。
- 追加、 **Azure Custom Vision Tensorflow モデル**エッジ モジュールには、コンテナーに格納されているイメージを分析するコードにします。
- 分析結果のメッセージを送信する、モジュールの設定に戻す、 **IoT Hub Service**します。
- 使用して、 **Azure Function App**内でメッセージを格納する、 **Azure Table**します。
- 設定する**Power BI**を格納されたメッセージを収集してレポートを作成します。
- 内で IoT メッセージ データを視覚化する**Power BI**します。

使用するサービスは次のとおりです。

- **Azure IoT Hub**により、接続、監視、および IoT 資産の管理、開発者が Microsoft Azure サービスです。 詳細については、次を参照してください。、 [ **Azure IoT Hub Service**ページ](https://azure.microsoft.com/en-au/services/iot-hub/)します。

- **Azure Container Registry**は、開発者がさまざまな種類のコンテナーのコンテナー イメージを格納する Microsoft Azure サービスです。 詳細については、次を参照してください。、 [ **Azure コンテナー レジストリ サービス**ページ](https://azure.microsoft.com/en-au/services/container-registry/)します。

- **Azure Function App**開発者が小規模なコードを実行する、Microsoft Azure のサービス '関数'、Azure では、します。 これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。 **Azure Functions** C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。 詳細については、次を参照してください。、 [ **Azure Functions**ページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。

- **Azure Storage:テーブル**Microsoft Azure サービスで、開発者が格納する構造化、非 SQL、データ、クラウドで任意の場所で簡単にアクセスできるようにします。 サービスは、スキーマなしの設計は幅広いプラットフォーム、必要に応じて、テーブルの進化のことができます、非常に柔軟なは。 詳細については、次を参照してください、 [ **Azure Tables**ページ。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

このコースでは、セットアップし、IoT Hub サービスを使用し、デバイスによって提供される応答を視覚化する方法を説明します。 までにビルドしている場合カスタムの IoT Hub サービス設定でこれらの概念を適用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 313:IoT Hub サービス</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

Microsoft HoloLens などの複合現実での開発の最新の前提条件をご覧ください、[ツールをインストールする](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)記事。

> [!NOTE]
> このチュートリアルは、Python を使用した基本的な経験を持っている開発者向けに設計されています。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)記事、ただし、このコースの情報が一致は完全にするよりも下に示す新しいソフトウェアで表示されますは仮定されません。

次のハードウェアとソフトウェアが必要です。

- Windows 10 Fall Creators Update (またはそれ以降)**開発者モードが有効になっています。**

    > [!WARNING]
    > Windows 10 Home エディションで、HYPER-V を使用して仮想マシンを実行することはできません。

- Windows 10 SDK (最新バージョン)
- HoloLens、a**開発者モードが有効になっています。**
- Visual Studio 2017.15.4 (Azure のクラウド エクスプ ローラーへのアクセスにのみ使用)
- Azure、および IoT Hub サービスのインターネット アクセス。 詳細についてに従ってくださいこの[IoT Hub サービスのページへのリンク](https://azure.microsoft.com/en-au/services/iot-hub/)
- 機械学習モデル。 モデルを使用する準備がない[、このコースで提供されるモデルを使用する](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)します。
- **HYPER-V**ソフトウェア、Windows 10 開発用コンピューターで有効にします。
- 開発用コンピューターまたは別の方法として実行されている Ubuntu (16.4 または 18.4) を実行する仮想マシンには、Linux (Ubuntu 16.4 または 18.4) を実行している別のコンピューターを使用できます。 HYPER-V を使用して、Windows 上の VM を作成する方法の詳細についてを見つけることができます、 [「開始前の準備」の章](#before-you-start)(。 https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>開始前の作業

1. 設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。
2. 実行することをお勧め**調整**と**センサー チューニング**(も役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときにします。

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

3. セットアップ、 **Ubuntu 仮想マシン**を使用して**HYPER-V**します。 次のリソースでプロセスを役立ちます。
    1.  最初に、このリンクに従う[16.04.4 の Ubuntu LTS (Xenial Xerus) の ISO をダウンロード](http://au.releases.ubuntu.com/16.04/)します。 選択、 **64 ビット PC (AMD64) デスクトップ イメージ**します。
    2.  確認**HYPER-V**は、Windows 10 コンピューターで有効になっています。 ガイダンスについては、このリンクをフォローできます[インストールと Windows 10 で HYPER-V を有効化](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)します。
    3.  HYPER-V を開始し、新しい Ubuntu VM を作成します。 このリンクを利用できる、 [、HYPER-V と VM を作成する方法についてステップ バイ ステップ ガイド](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)します。 要求されると **「ブート イメージ ファイルからオペレーティング システムをインストールする」** を選択、 **Ubuntu ISO**以前ダウンロードがあります。

    > [!NOTE]
    > 使用して **、HYPER-V のクイック作成**はお勧めしません。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第 1 章 - カスタム ビジョン モデルを取得します。

このコースにアクセスすること、[構築済みのカスタム ビジョン モデル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)キーボードとマウスの画像から検出します。 これを使用する場合に進みます[第 2 章](#chapter-2---the-container-registry-service)します。

ただし、独自のカスタム ビジョン モデルを使用する場合は、次の手順にできます。

1. **カスタム ビジョン プロジェクト**に移動して、**パフォーマンス**タブ。

    > [!WARNING]
    > モデルを使用する必要があります、 *compact*ドメイン モデルをエクスポートします。 プロジェクトの設定でドメイン モデルを変更できます。

    ![[パフォーマンス] タブ](images/AzureLabs-Lab313-01.png)

2. 選択、**イテレーション**エクスポートし、をクリックする**エクスポート**します。 ブレードが表示されます。

    ![ブレードをエクスポートします。](images/AzureLabs-Lab313-02.png)

3. ブレードで、 **Docker ファイル**します。

    ![docker を選択します。](images/AzureLabs-Lab313-03.png)

4. クリックして**Linux**クリックしてドロップダウン メニューで**ダウンロード**します。

    ![ダウンロードをクリックします。](images/AzureLabs-Lab313-04.png)

5. コンテンツを解凍します。 このコースで後ほど使用します。

## <a name="chapter-2---the-container-registry-service"></a>第 2 章 - コンテナー レジストリ サービス

**コンテナー レジストリ サービス**は、コンテナーをホストするために使用するリポジトリです。

**IoT Hub サービス**ビルドし、使用して、このコースでは参照する**コンテナー レジストリ サービス**Edge デバイスにデプロイするコンテナーを取得します。

1. 最初に、これに従って[Azure ポータルへのリンク](https://portal.azure.com/)、資格情報を使用してログインします。

2. 移動して**リソースの作成**を探して**Container Registry**します。

    ![コンテナー レジストリ](images/AzureLabs-Lab313-05.png)

3. をクリックして**作成**です。

    ![](images/AzureLabs-Lab313-06.png)

4. サービスのセットアップ パラメーターを設定します。

    1. この例では、プロジェクトの名前を挿入、呼び出された**IoTCRegistry**します。

    2. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

    3. サービスの場所を設定します。

    4. 設定**管理者ユーザー**に**を有効にする**します。

    5. 設定**SKU**に**基本的な**します。 

    ![](images/AzureLabs-Lab313-07.png)

5. クリックして**作成**し、サービスを作成するまで待ちます。 

6. 通知はポップアップ通知が正常に作成すると、 *Container Registry*、 をクリックして**リソースに移動**サービス ページにリダイレクトします。

    ![](images/AzureLabs-Lab313-08.png)

7. *Container Registry*サービス ページで、をクリックして**アクセス キー**します。

8. メモしてをおきます (、メモ帳を使用する可能性があります)、次のパラメーター。
    1. **ログイン サーバー**
    2. **Username**
    3. **Password**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第 3 章 - IoT Hub サービス

作成とのセットアップを開始するようになりました、 **IoT Hub Service**します。

1. サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。

2.  ログインすると、をクリックして**リソースの作成**左上隅にある検索して**IoT Hub**、 をクリック**Enter**します。

 ![ストレージ アカウントの検索](images/AzureLabs-Lab313-10.png)

3.  新しいページがの説明を入力、**ストレージ アカウント**サービス。 このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、サービスのこのインスタンスを作成します。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-11.png)

4.  クリックすると**作成**パネルが表示されます。

    1. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。


    2. 適切な選択**場所**(同じ場所でこのコースを作成するすべてのサービスを使用して)。

    3. 必要な挿入**名前**このサービス インスタンス。    

5.  ページの下部にある をクリックして**次へ。サイズとスケール**します。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-12.png)

6.  このページで、選択、**価格とスケールティア**(最初の IoT Hub サービス インスタンスの場合は、free レベルできるようにする)。  

7.  をクリックして**確認および作成**です。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-13.png)

8.  設定を確認して、をクリックして**作成**です。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-14.png)

9. 通知はポップアップ通知が正常に作成すると、 *IoT Hub*サービス、 をクリックして**リソースに移動**サービス ページにリダイレクトします。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-15.png)

10. 左側のサイド パネルに表示されるまでスクロール*デバイスの自動管理*、 をクリック**IoT Edge**します。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-16.png)

11. 右側に表示されるウィンドウでクリックして**IoT Edge デバイスの追加**します。 ブレードが右側に表示されます。

12. ブレードで、新しいデバイスを提供する**デバイス ID** (好みの名前)。 をクリックし、**保存**します。 *プライマリ*と*セカンダリ キー*は自動生成があれば**の自動生成**オンします。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-17.png)

13. 移動するが、 *IoT Edge デバイス* セクションで、新しいデバイスが表示されます。 新しいデバイスをクリックします (で赤で、イメージの下)。 

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-18.png)

14. *デバイスの詳細*が表示されたら、ページのコピーを作成する、**接続文字列**(主キー)。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-19.png)

15. 、左側のパネルに戻り、をクリックして*共有アクセス ポリシー*、を開きます。 

16. 表示されるページで、をクリックして**iothubowner**、し、画面の右側のブレードが表示されます。 

17. 書き留めて (上、メモ帳)、**接続文字列**(主キー) を設定するときに、後で使用、*接続文字列*デバイスにします。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第 4 章 - 開発環境を設定します。

作成、展開用モジュール*IoT Hub の Edge*、Windows 10 を実行している開発用コンピューターにインストールされている、次のコンポーネントが必要になります。

1.  [Windows の docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)、ダウンロードできるようにするアカウントを作成するよう求められます。 

    [![windows の docker をダウンロードします。](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker 必要があります*Windows 10 PRO*、 *Enterprise 14393*、または*Windows Server 2016 RTM*を実行します。 その他のバージョンの Windows 10 を実行している場合、Docker を使用してをインストールしてくださいことができます、 [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)します。

2.  [Python 3.6](https://www.python.org/downloads/)します。

    [![python 3.6 をダウンロードします。](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (VS Code とも呼ばれます)](https://code.visualstudio.com/download)します。

    [![VS Code をダウンロードします。](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

上記で説明したソフトウェアのインストール後は、コンピューターを再起動する必要があります。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第 5 章 - Ubuntu 環境のセットアップ

デバイスのセットアップ移動できますようになりました**Ubuntu OS を実行している**します。 ボード上、コンテナーをデプロイするために必要なソフトウェアをインストールするのには、下の手順に従います。

> [!IMPORTANT]
> ターミナル、コマンドの前に常に**sudo**管理者ユーザーとして実行します。 つまり、します。
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  開く、 **Ubuntu のターミナル**、次のコマンドを使用してインストールして**pip**:

    > [!ヒント] を開く*ターミナル*キーボード ショートカットを使用して非常に簡単に使用します。**Ctrl + Alt + T**します。

    ```bash
        sudo apt-get install python-pip
    ```

2.  この章では、する必要があります、によって*ターミナル*デバイス ストレージを使用するアクセス許可、および入力するを**はい/いいえ**(はいまたは no)、型 **'y'**、キーを押しますと、**Enter**を受け入れるためのキー。

3.  そのコマンドが完了すると、次のコマンドを使用してをインストールする**curl**:

    ```bash
        sudo apt install curl
    ```

4.  1 回**pip**と**curl**は、次のコマンドを使用してインストールする、インストールされている、 **IoT Edge ランタイム**を展開し、ボード上のモジュールを制御するために必要になります。

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. この時点で求められますを開く、*ランタイム構成ファイル*、挿入する、 **Device Connection String**、(、メモ帳で)、メモしたを作成するとき、 **IoT Hub サービス** ([第 3 章の手順 14 で](#chapter-3---the-iot-hub-service))。 そのファイルを開くターミナルで次の行を実行します。

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. **Config.yaml**ファイルが表示されている、編集するための準備完了になります。

    > [!WARNING]
    > このファイルが開いたら、やや混乱を招く場合があります。 テキスト内で、このファイルを編集する必要がある、*ターミナル*自体。 

    1.  キーボードの矢印キーを使用して、スクロール ダウン (少し方法下へスクロールする必要があります) を含む行に到達する"。

        "**\<デバイス接続文字列をここでの追加 &GT;**"。

    2. 行を置き換える **、中かっこも含め**で、**デバイスの接続文字列**先ほどメモします。

7. キーボードの場所に、接続文字列とキーを押して、 **CTRL + X**キー ファイルを保存します。 」と入力して確認するよう求められます**Y**します。次に、キーを押して、 **」と入力**キーを確認します。 通常に戻り、*ターミナル*します。 

8. インストールがこれらのコマンドがすべて正常に実行すると、 **IoT Edge ランタイム**します。 初期化されると、ランタイムは、デバイスの電源が入っている独自たびに開始して、バック グラウンドでモジュールから展開するを待つ内に配置されます、 **IoT Hub Service**します。

9.  初期化するために次のコマンドラインの実行、 *IoT Edge ランタイム*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > .Yaml ファイル、または上記の設定を変更する場合、上記の再起動の行を再度実行する必要があります。 内*ターミナル*します。

10. チェック、 *IoT Edge ランタイム*次のコマンドラインを実行している別の状態。 ランタイムが、状態で表示される必要があります**アクティブ (実行中)** を緑のテキスト。

    ```bash
        sudo systemctl status iotedge
    ```

11. キーを押して、 **Ctrl + C**キー、状態 ページを終了します。 確認することができます、 *IoT Edge ランタイム*次のコマンドを入力して、コンテナーを正しく引いています。

    ```bash
        sudo docker ps
    ```

12. 2 つのコンテナーの一覧が表示されます。 これらは、IoT Hub サービス (edgeAgent および edgeHub) によって自動的に作成される既定のモジュールです。 作成して、独自のモジュールを展開すると、既定の下に、この一覧に表示されます。

## <a name="chapter-6---install-the-extensions"></a>第 6 章 - 拡張機能をインストールします。

> [!IMPORTANT]
> 次のいくつかの章 (6 ~ 9) では、Windows 10 コンピューターで実行します。

1. 開いている**VS Code**します。

2. をクリックして、**拡張機能**(正方形) ボタンの左側の VS、バーコードを開く、**拡張機能パネル**します。

3. 検索し、インストールの場合は、(次の図に示すように)、次の拡張機能。

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![コンテナーを作成します。](images/AzureLabs-Lab313-24.png)

4. 拡張機能がインストールされると、VS Code を再度開くを閉じています。

5. VS Code で、もう一度開きに移動します**ビュー > 統合ターミナル**します。

6. インストールするようになりました**Cookiecutter**します。 ターミナルで次の bash コマンドを実行します。

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!ヒント] で次のコマンドに問題がある場合: 
    >1. VS Code、および/またはコンピューターを再起動します。
    >2. 切り替える必要があります、 **VS Code ターミナル**を使用してつまり、Python をインストールする 1 つ**Powershell** (特に場合に、Python 環境は、コンピューターに既にインストールされている)。 ターミナルを開き、端末の右側にあるメニューのドロップダウンが表示されます。
     ![コンテナーを作成します。](images/AzureLabs-Lab313-24b.png) 
    >3. 確認、 **Python**としてのインストール パスが追加されます**環境変数**コンピューターにします。 Cookiecutter は、同じロケーション パスの一部にする必要があります。 これに従ってください[環境変数の詳細については、リンク](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)、 

7. 1 回**Cookiecutter** 、インストールが完了した、コンピューターを再起動する必要がありますように**Cookiecutter**はシステムの環境でのコマンドとして認識します。

## <a name="chapter-7---create-your-container-solution"></a>7 -」の章のコンテナー ソリューションを作成します。

この時点では、モジュールにプッシュされると、コンテナーを作成する必要があります、 *Container Registry*します。 使用するコンテナーをプッシュすると、 *IoT Hub の Edge*を実行しているデバイスにデプロイするサービス、 *IoT Edge ランタイム*します。

1. VS Code からクリックして**ビュー > コマンド パレット**します。

2. パレットで、検索し、実行**Azure IoT Edge:新しい Iot Edge ソリューション**します。

3. ソリューションを作成する場所を参照します。 キーを押して、 **」と入力**キー、場所をそのままにします。

4. ソリューションに名前を付けます。 キーを押して、 **Enter**キーを指定された名前を確認します。

5. 今すぐ求め、ソリューション テンプレートの framework を選択します。 クリックして**Python モジュール**します。 キーを押して、 **Enter**キーは、この選択内容を確認します。

6. モジュールの名前を付けます。 キーを押して、 **Enter**キーをモジュールの名前を確認します。 後で使用するために、モジュール名 (、メモ帳) をメモしてを実行することを確認してください。

7. 構築済みわかります*Docker イメージ リポジトリ*パレットにアドレスが表示されます。 次のようになります。

    **localhost:5000/名前、モジュールの**します。 

8. 削除**localhost:5000**、およびその場所の挿入、*Container Registry* **ログイン サーバー**アドレスで、作成するときにメモしておいた、**コンテナーレジストリ サービス**([手順 8、第 2 章の](#chapter-2---the-container-registry-service))。 キーを押して、 **Enter**キー、アドレスを確認します。

9. この時点で、テンプレート、Python モジュールを含むソリューションが作成され、その構造が表示されます、**探索タブ**画面の左側にある、VS Code の。 場合、**探索タブ**が開いていない場合、開くことができますが、左側のバーで、最上位のボタンをクリックしています。

    ![コンテナーを作成します。](images/AzureLabs-Lab313-25.png)

10. この章の最後の手順は、をクリックして開く、 **.env ファイル**、内から、 **タブの調査**、追加、 *Container Registry* **ユーザー名**と**パスワード**します。 このファイルは、git によって無視されますが、コンテナーでは、ビルドにへのアクセスに資格情報の設定は、**コンテナー レジストリ サービス**します。

    ![コンテナーを作成します。](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第 8 章 - コンテナー ソリューションの編集

今すぐは、次のファイルを更新することで、コンテナー ソリューションを行います。

- *メイン<span></span>.py* python スクリプト。
- *requirements.txt*します。
- *deployment.template.json*します。
- *Dockerfile.amd64*

作成して、*イメージ*と照合するイメージを確認する python スクリプトで使用される、フォルダー、*カスタム ビジョン モデル*します。 最後に、追加、 *labels.txt* 、モデルを読み取るためのファイルと*model.pb*ファイルで、これは、モデルです。

1. VS Code で開き、モジュール フォルダーに移動し、という名前のスクリプトを探して**メイン<span></span>.py**します。 ダブルクリックして開きます。

2. ファイルの内容を削除し、次のコードを挿入します。

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  というファイルを開く**requirements.txt**、その内容を次に置き換えます。

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  というファイルを開く**deployment.template.json**、その次のコンテンツを置き換えると、以下のガイドライン。

    1. 自分で、一意の JSON 構造を必要があります、ため (例をコピー) ではなく手動で編集する必要があります。 簡単にするを使用して、次のガイドとして画像。
    2. 次に、さまざまな領域がある**は変更しないでくださいは黄色で強調表示**します。
    3. **を削除する必要があるセクションでは、強調表示されている red です。**
    4. 正しいの角かっこを削除するように注意してくださいし、も、コンマを削除します。

        ![コンテナーを作成します。](images/AzureLabs-Lab313-27.png)

    5. 完了した JSON は、次の図のようになります (一意の相違点は、サーバーでは、:*モジュール/ユーザー名/パスワード/モジュール名参照*)。

        ![コンテナーを作成します。](images/AzureLabs-Lab313-28.png)

5.  というファイルを開く**Dockerfile.amd64**、その内容を次に置き換えます。

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  下にフォルダーを右クリックして**モジュール**(以前; 指定した名前になりますで例をそれをさらに、呼び出されます*pythonmodule*)、 をクリック**新しいフォルダー**. フォルダーの名前**イメージ**します。

7.  フォルダー内には、マウスまたはキーボードを含む一部のイメージを追加します。 イメージ、Tensorflow モデルによって分析されるものになります。

    > [!WARNING]
    > 独自のモデルを使用している場合は、独自のモデル データを反映するようにこれを変更する必要があります。

8.  取得する必要がありますこれで、 **labels.txt**と**model.pb**以前ダウンロード モデル フォルダーからファイルを (または独自から作成した**Custom Vision Service**) で[第 1 章](#chapter-1---retrieve-the-custom-vision-model)します。 ファイルを作成したら、その他のファイルと共に、ソリューション内でそれらを配置します。 最終的な結果は、次の図のようになります。

    ![コンテナーを作成します。](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第 9 章 – パッケージのコンテナーとしてソリューション

1.  コンテナーとして、ファイルを「パッケージ」し、それをプッシュする準備が整いました、 **Azure Container Registry**します。 VS Code 内で開く、*統合ターミナル*(**ビュー > 統合ターミナル/CTRL + '**) へのログインに次の行を使用して**Docker** (の値に置き換えてください、コマンドの資格情報を**Azure Container Registry (ACR)**)。

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. ファイルを右クリックして**deployment.template.json**、 をクリック**IoT Edge ソリューションのビルド**します。 このビルド プロセス (デバイス) によってはかなり時間のかかるので、待機します。 ビルド プロセスが完了した後、 **deployment.json**という名前の新しいフォルダー内のファイルが作成されているが**config**します。

    ![デプロイを作成します。](images/AzureLabs-Lab313-30.png)

3. 開く、**コマンド パレット**、もう一度検索して**Azure:サインイン**します。 Azure アカウントの資格情報以外を使用して、画面の指示をに従ってください。VS Code の提供するためのオプション*コピーして開く*、どちらの間もなくし、既定の web ブラウザーを開きますが、デバイス コードをコピーします。 メッセージが表示されたら、コンピューターの認証に、デバイス コードを貼り付けます。

    ![コピーを開きます](images/AzureLabs-Lab313-31.png)

4. 表示されますの下にある符号付き 1 回、*探索*パネル、という名前の新しいセクション**Azure IoT Hub デバイス**します。 展開するには、このセクションをクリックします。

    ![エッジ デバイス](images/AzureLabs-Lab313-32.png)

5. デバイスがここではない場合を右クリックする必要があります。 *Azure IoT Hub デバイス*、をクリックし、 **IoT Hub 接続文字列の設定**します。 表示されますが、**コマンド パレット**(VS Code の上部) にはプロンプトで入力する、*接続文字列*します。 これは、*接続文字列*の最後にメモした[第 3 章](#chapter-3---the-iot-hub-service)します。 キーを押して、 **Enter**で文字列をコピーした後、キーします。    

6. デバイスは、読み込み、および表示する必要があります。 デバイス名を右クリックし、をクリック**1 つのデバイスの Create Deployment**します。

    ![デプロイを作成します。](images/AzureLabs-Lab313-33b.png)

7. 表示されます、*ファイル エクスプ ローラー*プロンプトに移動することができます、 **config**フォルダー、および選択し、 **deployment.json**ファイル。 そのファイルを選択すると、クリックして、 **Edge 配置マニフェストの選択**ボタンをクリックします。

    ![デプロイを作成します。](images/AzureLabs-Lab313-34.png)

8. この時点で指定した、 **IoT Hub Service**マニフェスト モジュールとしてから、コンテナーをデプロイするために、 **Azure Container Registry**、実質的に、デバイスに展開します。

9. デバイスから IoT Hub に送信されるメッセージを表示するには、もう一度右クリックで、デバイス名を**Azure IoT Hub デバイス**セクションで、**エクスプ ローラー**パネルをクリックします**監視の開始D2C メッセージ**します。 VS ターミナルで、デバイスから送信されたメッセージが表示されます。 患者に、これは時間がかかります。 デバッグ、および配置が成功したかどうかにチェックの次の章を参照してください。

内のイメージ間でこのモジュールに処理され、今すぐ、**イメージ**フォルダーの各イテレーションで分析したりと。 これは、単なる明らかに、IoT Edge デバイスの環境で動作する基本的な機械学習モデルを取得する方法のデモンストレーションです。 

この例の機能を展開するには、いくつかの方法で続行する可能性があります。 デバイスに接続されていて、images フォルダーにイメージを保存します。 web カメラから写真をキャプチャすると、コンテナーで 1 つの方法をいくつかのコードなどでした。 

別の方法でしたするイメージのコピー、IoT デバイスからコンテナーにします。 そのための実用的な方法では、IoT デバイス (おそらく小規模なアプリがジョブを実行、プロセスを自動化する場合) のターミナルで次のコマンドを実行します。 このコマンドをテストするには、ファイルが格納されているフォルダーの場所から手動で実行します。

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第 10 章 - IoT Edge ランタイムのデバッグ

コマンドライン、および監視およびのメッセージング アクティビティをデバッグするためのヒントの一覧を次に、 *IoT Edge ランタイム*から、 **Ubuntu デバイス**します。 

- チェック、 *IoT Edge ランタイム*次のコマンドラインを実行している別の状態。

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > キーを押すように**Ctrl + C**ステータスの表示が完了する。

- 現在展開されているコンテナーを一覧表示します。 場合、 *IoT Hub Service*コンテナーを正常にデプロイが次のコマンドラインを実行してが表示されます。

    ```bash
        sudo iotedge list
    ```

    または

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 上記の適しているかどうか、モジュールのデプロイが正常にリストに表示されるかを確認するにはそれ以外の場合は、**のみ**を参照してください、 *edgeHub*と*edgeAgent*します。

- コンテナーのコードのログを表示するには、次のコマンドラインを実行します。

    ```bash
        journalctl -u iotedge
    ```

**IoT Edge ランタイムを管理する便利なコマンド:**

-  ホストのすべてのコンテナーを削除します。

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  停止する、 *IoT Edge ランタイム*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>章 11 - Table Service を作成します。 

ストレージ リソースを作成して、Azure テーブル サービスを作成する、Azure Portal に移動します。

1. サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。

2. ログインすると、をクリックして**リソースの作成**、左上の検索および上隅にある**ストレージ アカウント**、キーを押すと、 **」と入力**キー、検索を開始します。

3. 表示されていますとクリックして**ストレージ アカウント - blob、ファイル、テーブル、キュー**一覧から。

    ![ストレージ アカウントの検索](images/AzureLabs-Lab313-35.png)

4. 新しいページがの説明を入力、**ストレージ アカウント**サービス。 このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、サービスのこのインスタンスを作成します。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab313-36.png)

5. クリックすると**作成**パネルが表示されます。

    1. 必要な挿入**名前**このサービス インスタンスの (*すべて小文字である必要があります*)。

    2. **デプロイ モデル**、 をクリックして**Resource manager**します。

    3. **アカウントの種類**、ドロップダウン メニューを使用して、クリックして**ストレージ (汎用 v1)** します。

    4. 適切なクリックして**場所**します。
    
    5. **レプリケーション**ドロップダウン メニューで、をクリックして**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。

    6. **パフォーマンス**、 をクリックして**標準**します。

    7. 内で、**転送が必須のセキュリティで保護された**セクションで、**無効**します。

    8. **サブスクリプション**ドロップダウン メニューで、適切なサブスクリプションをクリックします。

    9. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    10. まま**仮想ネットワーク**として**無効になっている**するためのオプションは、この場合、します。

    11. **[作成]** をクリックします。

        ![ストレージの詳細を入力します。](images/AzureLabs-Lab313-37.png)

6. クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

7. 通知は、サービス インスタンスが作成されたら、ポータルに表示されます。 新しいサービス インスタンスを探索する通知をクリックします。

    ![新しい記憶域の通知](images/AzureLabs-Lab313-38.png)

8. をクリックして、**リソースに移動**通知で、[新しい記憶域のサービス インスタンスの概要] ページが表示されます。

    ![リソースに移動します。](images/AzureLabs-Lab313-39.png)

9. 概要 ページの右側にあるをクリックします。**テーブル**します。
    
    ![テーブル](images/AzureLabs-Lab313-40.png)

10. 右側のパネルを表示する変更は、 **Table Service**については、の新しいテーブルを追加する必要があります。 クリックして、 **+ テーブル**ボタンの左上隅をクリックします。

    ![テーブルを開く](images/AzureLabs-Lab313-41.png)

11. 入力する必要があります、新しいページが表示されます、**テーブル名**します。 これは、(関数アプリ、および Power BI の作成) 以降の章で、アプリケーションでデータを指すために使用する名前です。 挿入**IoTMessages**名として (、独自に選択することができますので、このドキュメントの後半で使用する場合) をクリック**OK**します。 

12. 新しいテーブルが作成されたら、できなく内を確認する、 **Table Service** (下部) のページ。

    ![新しいテーブルの作成](images/AzureLabs-Lab313-42.png)  

13. 今すぐクリックして**アクセス キー**のコピーを作成し、**ストレージ アカウント名**と**キー** (、メモ帳を使用)、これらの値は使用、このコースの後半で作成するときに、**Azure Function App**します。

    ![新しいテーブルの作成](images/AzureLabs-Lab313-43.png) 

14. までスクロールし、左側のパネルを使用して、 *Table Service*セクションをクリックします**テーブル**(または**参照テーブル**、新しいポータル) のコピーを作成し、 **テーブルの URL** (、メモ帳を使用)。 テーブルをリンクするときに、このコースの後半でこの値が使用されます、 **Power BI**アプリケーション。

    ![新しいテーブルの作成](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第 12 章 - Azure テーブルの完了

これで、 **Table Service**ストレージ アカウントを設定したら、情報格納および取得するために使用するデータを追加する時間。 テーブルの編集を実行できます**Visual Studio**します。

1. 開いている**Visual Studio** (**いない**Visual Studio Code)。

2. メニューから、次のようにクリックします。**ビュー > Cloud Explorer**します。

    ![クラウド エクスプ ローラーを開く](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer** (に患者、読み込み時間がかかる場合があります) がドッキングされている項目として開きます。

    > [!WARNING] 
    > サブスクリプションの作成に使用する場合、*ストレージ アカウント*が表示されないできることを確認します。 
    > - Azure Portal を使用したものと同じアカウントにログインします。
    > - (アカウント設定からフィルターを適用する必要があります)、アカウントの管理ページからサブスクリプションを選択します。  
    >
    >   ![サブスクリプションが見つかりません](images/AzureLabs-Lab313-46.png)

4. Azure クラウド サービスが表示されます。 検索**ストレージ アカウント**アカウントを展開するの左側にある矢印をクリックします。

    ![ストレージ アカウント を開きます](images/AzureLabs-Lab313-47.png)

5. 展開されている場合、新しく作成した後**ストレージ アカウント**できるようにします。 ストレージの左側にある矢印をクリックしを展開したら探します**テーブル**を表示する横の矢印をクリックします、**テーブル**最後の章で作成しました。 ダブルクリックして、**テーブル**します。

6. テーブルには、Visual Studio ウィンドウの中央に開かれます。 テーブル アイコンをクリックして、 **+** には、(+)。

    ![新しいテーブルを追加します。](images/AzureLabs-Lab313-48.png)

7. ウィンドウがするためのプロンプトを表示する表示*エンティティの追加*します。 3 つのプロパティである必要が 1 つだけのエンティティを作成します。 わかります*PartitionKey*と*RowKey*が既に提供されている、使用される場合は、テーブルでデータを検索します。 

    ![パーティションと行キー](images/AzureLabs-Lab313-49.png)

8. 次の値を更新します。

    - 名前:**PartitionKey**値。**PK_IoTMessages** 

    - 名前:**RowKey**値。**RK_1_IoTMessages** 

9. をクリックし、**プロパティを追加**(の左下に、*エンティティの追加*ウィンドウ) し、次のプロパティを追加します。

    - **MessageContent**、として、*文字列*値を空のままにします。

10. 次の図に、テーブルと一致する必要があります。

    ![正しい値を追加します。](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > エンティティの数 1、行キーでがなぜ理由ためにである可能性があります、複数のメッセージを追加する実験をご希望する必要がありますこのコースでさらにします。

11. クリックして**OK**は終了するとき。 テーブルには、使用する準備ができました。

## <a name="chapter-13---create-an-azure-function-app"></a>章 13 - Azure Function App を作成します。 

作成に時間をここでは、 *Azure Function App*、によって呼び出される、 *IoT Hub Service*を格納する、 *IoT Edge*デバイスにメッセージが、 **テーブル**サービスは、前の章で作成しました。

最初に、必要なライブラリの読み込みに、Azure 関数を許可するファイルを作成する必要があります。

1.  開いている**メモ帳**(キーを押して、 *Windows キー*、および種類*メモ帳*)。

    ![メモ帳を開く](images/AzureLabs-Lab313-51.png)

2.  メモ帳を開く、そこに以下の JSON 構造を挿入します。 完了したら、としてデスクトップに保存**project.json**します。 このファイルは、関数を使用してライブラリを定義します。 NuGet を使用した場合は、使い慣れたが検索されます。
    
    > [!WARNING]
    > 名前の付け方が正しい; 重要です。確認は **、.txt が付いていない**ファイル拡張子。 参照に以下をご覧ください。
    >
    > ![保存の JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  [Azure ポータル](https://portal.azure.com) にログインします。

4.  ログインした後は、をクリックして**リソースの作成**左上隅にある検索して**Function App**、キーを押すと、 **」と入力**キーを検索します。 クリックして*Function App*結果から、新しいパネルを開きます。

    ![関数アプリの検索](images/AzureLabs-Lab313-53.png)

5.  新しいパネルがの説明を入力、 **Function App**サービス。 このパネルの下部にある左はで、をクリックして、**作成**ボタンは、この関連付けサービスを作成します。

    ![関数アプリ インスタンス](images/AzureLabs-Lab313-54.png)

6.  クリックすると**作成**次を入力します。

    1. **アプリ名**、このサービス インスタンスのご希望の名前を挿入します。

    2. 選択、**サブスクリプション**します。

    3. 作成時刻の場合、これは、最初に、適切な価格レベルを選択、 **Function App サービス**、free レベルを使用することがあります。

    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニング、アクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. **OS**、目的のプラットフォームであるために、Windows をクリックします。

    6. 選択、**ホスティング プラン**(このチュートリアルを使用して、**従量課金プラン**します。

    7. 選択、**場所**(前の手順で作成したストレージと同じ場所を選択)

    8. **ストレージ**セクション **、前の手順で作成したストレージ サービスを選択する必要があります**します。

    9. 必要はありません*Application Insights*このアプリでため、自由に**オフ**します。

    10. **[作成]** をクリックします。

        ![新しいインスタンスを作成します。](images/AzureLabs-Lab313-55.png)

7.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

8.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![新しい通知](images/AzureLabs-Lab313-56.png)

9.  デプロイが成功すると、通知をクリックします (終了)。

10. をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 

    ![リソースに移動します。](images/AzureLabs-Lab313-57.png)

11. 新しいパネルの左側にある クリックして、 **+** (隣にアイコン +)*関数*、新しい関数を作成します。

    ![新しい関数を追加します。](images/AzureLabs-Lab313-58.png)

12. 中央のパネル内、**関数**作成ウィンドウが表示されます。 さらに、下にスクロールし、をクリックして**カスタム関数**します。

    ![カスタム関数](images/AzureLabs-Lab313-59.png)

13. 次のページが表示されるまで下へスクロール**IoT Hub (イベント ハブ)** の順にクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-60.png)

14. **IoT Hub (イベント ハブ)** ブレードで、設定、**言語**に**C#** し、**新しい**します。

    ![カスタム関数](images/AzureLabs-Lab313-61.png)

15. このウィンドウは表示されますが、ことを確認します**IoT Hub**が選択されているとの名前、 *IoT Hub*の名前を持つ対応するフィールド、 *IoT Hub サービス*必要のあります。以前に作成 ([手順 8、第 3 章の](#chapter-3---the-iot-hub-service))。 をクリックし、**選択**ボタンをクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-62.png)

16. 戻り、 **IoT Hub (イベント ハブ)** ブレードで、クリック**作成**です。

    ![カスタム関数](images/AzureLabs-Lab313-63.png)

17. 関数エディターにリダイレクトされます。

    ![カスタム関数](images/AzureLabs-Lab313-64.png)

18. すべてのコードを削除し、次のように置き換えます。

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 適切な値に対応するように、次の変数を変更 (**テーブル**と**ストレージ**値から[11、13 をそれぞれ、第 11 章の手順](#chapter-11---create-table-service))、使用される、**ストレージ アカウント**:

    - **tableName**の名前を持つ、**テーブル**内にある、**ストレージ アカウント**します。
    - **tableURL**の URL を使用して、**テーブル**内にある、**ストレージ アカウント**します。
    - **storageAccountName**の名前に対応する値の名前を持つ、**ストレージ アカウント**名。
    - **storageAccountKey**、以前に作成したストレージ サービスで取得したキーを使用します。

    ![カスタム関数](images/AzureLabs-Lab313-65.png)

20. コードの場所で、次のようにクリックします。**保存**します。

21. 次に、クリックして、 **\<** (矢印) アイコンをページの右側にあります。

    ![カスタム関数](images/AzureLabs-Lab313-66.png)

22. パネルは、右からにスライドします。 そのパネル で、**アップロード**、および*ファイル ブラウザー*が表示されます。

23. 、に移動し、クリックすると、、 **project.json**ファイルで、で作成した**メモ帳**以前は、順にクリックします、**オープン**ボタンをクリックします。 このファイルは、関数が使用するライブラリを定義します。

    ![カスタム関数](images/AzureLabs-Lab313-67.png)

24. ファイルがアップロードされると、右側のパネルに表示されます。 内で開くをクリックすると、**関数**エディター。 表示する必要があります**まったく**次のイメージと同じです。

    ![カスタム関数](images/AzureLabs-Lab313-68.png)

25. この時点でものメッセージを格納する、関数の機能をテストするよいでしょう、*テーブル*します。 ウィンドウの上部右側にある、 をクリックして**テスト**します。

    ![カスタム関数](images/AzureLabs-Lab313-69.png)

26. メッセージの挿入、**要求本文**で上の図に示すように、**実行**します。 

27. 関数が実行され、結果の状態を表示する (緑色で表示されます**ステータス 202 Accepted**、上記の*出力*ウィンドウで、正常な呼び出しが)。

    ![出力結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第 14 章 – アクティブなメッセージの表示

今すぐ Visual Studio を開く場合 (**いない**Visual Studio Code) で保存するように、テスト メッセージの結果を視覚化できます、 *MessageContent*領域の文字列します。

![カスタム関数](images/AzureLabs-Lab313-71.png)

Table Service で Function App と Ubuntu デバイスのメッセージが表示されます、 *IoTMessages*テーブル。 を実行していない場合、デバイスを再度起動して、Visual Studio を使用して、デバイス、および、テーブル内のモジュールから結果メッセージを表示することができます*Cloud Explorer*します。

![データを視覚化します。](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第 15 章「Power BI のセットアップ

セットアップは、IOT デバイスからデータを視覚化する**Power BI** (デスクトップのバージョン) からデータを収集、*テーブル*サービスで、先ほど作成しました。 *HoloLens*バージョンの Power BI を使用してそのデータを結果を視覚化します。

1.  Windows 10 の Microsoft Store を開き、検索**Power BI Desktop**します。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  アプリケーションをダウンロードします。 これには、ダウンロードが完了したら、したら、それを開きます。

3.  ログイン*Power BI*で、 **Microsoft 365 アカウント**します。 ブラウザー、サインアップにリダイレクトされます。 サインアップし、Power BI アプリに戻ってもう一度サインインします。

4.  をクリックして**データの取得**し、**より.**.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  クリックして**Azure**、 **Azure Table Storage**、をクリックして**Connect**します。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  挿入を求められます、**テーブル URL**以前に収集した ([第 11 章の 13 の手順で](#chapter-11---create-table-service))、Table Service の作成中にします。 URL を挿入した後は、テーブル「サブ フォルダー」(IoTMessages は、このコースでは) を参照するパスの部分を削除します。 次の図に表示される最終的な結果があります。 をクリックして**OK**します。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  挿入を求め、**ストレージ キー**書き留めた ([手順 11 第 11 章の](#chapter-11---create-table-service))、Table Storage を作成するときに以前。 をクリックして**Connect**します。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. A**ナビゲーター パネル**が表示されます、テーブルの横にあるボックスをオンにしをクリックして**ロード**します。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. テーブルが Power BI に読み込まれているようになりました、クエリが値を表示する必要しますが、あります。 これを行うにあるテーブル名を右クリックし、**フィールド パネル**画面の右側にあります。 をクリックして**クエリの編集**します。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. A **Power Query エディター**として、テーブルを表示する、新しいウィンドウが開きます。 [単語] をクリックして**レコード**内、*コンテンツ*格納されているコンテンツを視覚化する、テーブルの列。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. をクリックして**Into テーブル**ウィンドウの上部左にあります。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. をクリックして**閉じて適用**します。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 内で、クエリの読み込みが完了すると、**フィールド パネル**、画面の右側にある、パラメーターに対応するボックスをオンに**名前**と**値**を視覚化、 **MessageContent**列のコンテンツ。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. をクリックして、**青いディスク アイコン**で任意のフォルダーで作業内容を保存するには、ウィンドウの左上。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. ワークスペースに、テーブルをアップロードする [発行] ボタンをクリックすることができますようになりました。 メッセージが表示されたら、 をクリックして**個人用ワークスペース** をクリック*選択*します。 送信の成功した結果を表示するには待機します。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 次の章では、特定の HoloLens です。 Power BI は現在使用できません没入型アプリケーションとして Windows 混合現実ポータル (Cliff 家とも呼ばれます) で、デスクトップ バージョンを実行することができますが、デスクトップ アプリを使用します。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第 16 章 – HoloLens でデータを Power BI の表示

1. HoloLens へログイン、 **Microsoft Store**アプリケーションの一覧で、アイコンをタップします。

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. 検索し、ダウンロード、 **Power BI**アプリケーション。

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. 開始**Power BI**アプリケーションの一覧から。 

4. **Power BI**にログインするよう求められます可能性があります、 **Microsoft 365 アカウント**します。

5. 1 回、アプリ内次の図に示すように、ワークスペースが既定で表示します。 発生しない場合は、単にウィンドウの左側にあるワークスペース アイコンをクリックします。

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>IoT Hub のアプリケーションが完了しました

これで、シミュレートされた仮想マシンのエッジ デバイスで、IoT Hub サービスを作成しました。 デバイスは、machine learning のモデルを Power BI に読み取られ、Microsoft HoloLens 内で視覚化する Azure Function App によって容易になります、Azure Table Service の結果を通信できます。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

テーブルに格納されているメッセージの構造を展開し、グラフとして表示します。 多くのデータを収集し、後で表示される、同じテーブルに保存する場合があります。

### <a name="exercise-2"></a>手順 2

追加で作成するため、分析するカメラでイメージをキャプチャできます、IoT ボード上に展開する「カメラ キャプチャ」モジュール。
