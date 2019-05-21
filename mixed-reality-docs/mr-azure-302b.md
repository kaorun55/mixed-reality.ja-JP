---
title: MR と Azure 302b - Custom vision
description: 機械学習モデルをトレーニングする方法については、このコースを完了し、トレーニング済みモデルを使用して、複合現実のアプリケーション内で類似のオブジェクトを認識します。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、カスタム ビジョン、没入型、hololens、vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600001"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR と Azure 302b:カスタム ビジョン

このコースでは複合現実のアプリケーションで Azure の Custom Vision 機能を使用して、指定されたイメージ内でカスタム ビジュアルのコンテンツを認識する方法については。

このサービスを使用して、オブジェクトのイメージを使用して機械学習モデルのトレーニングにはできます。 Microsoft HoloLens または没入型の (VR) ヘッドセットの PC に接続されているカメラのカメラ キャプチャによって提供される、類似のオブジェクトを認識するのにトレーニング済みモデルを使用するされます。

![コースの結果](images/AzureLabs-Lab302b-00.png)

Azure の Custom Vision には、Microsoft の Cognitive サービスにより、カスタム イメージ分類モデルを構築する開発者ですが。 これらの分類モデルを認識して新しいイメージで、使用するまたは、その新しいイメージ内のオブジェクトを分類します。 サービスは、プロセスを合理化するシンプルで使いやすい、オンライン ポータルを提供します。 詳細については、次を参照してください。、 [Azure Custom Vision Service ページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)します。

このコースの完了したら、2 つのモードで動作できる必要が複合現実のアプリケーションが用意されます。

-   **分析モード**: Custom Vision Service 手動でセットアップ イメージをアップロードし、タグを作成し、トレーニング、サービスによって (このケースのマウスとキーボード) のさまざまなオブジェクトを認識します。 後は、カメラを使用してイメージをキャプチャし、現実の世界でこれらのオブジェクトを認識する HoloLens アプリを作成します。

-   **トレーニング モード**: は、アプリで「トレーニング モード」は有効にするコードを実装します。 トレーニング モードを使用すると、HoloLens のカメラを使用してイメージをキャプチャ、キャプチャしたイメージをサービスにアップロードし、カスタム ビジョン モデルをトレーニングできます。

このコースでは、Custom Vision Service から Unity に基づくサンプル アプリケーションに結果を取得する方法を説明します。 最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 302b:カスタム ビジョン</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。 (VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。 コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。

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
- (イマーシブ ヘッドセット開発) は、PC に接続されているカメラ
- Azure のセットアップおよび Custom Vision API 取得するためのインターネット アクセス
- 一連の少なくとも 5 (5) イメージ (10 (10) を推奨) を認識する Custom Vision Service を希望するオブジェクトごとにします。 使用することができる場合は、 [(コンピューターのマウスとキーボード) は、このコースで既に提供されているイメージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)します。

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1---the-custom-vision-service-portal"></a>第 1 章 - Custom Vision Service ポータル

使用する、 *Custom Vision Service* Azure では、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  最初に、[に移動し、 *Custom Vision Service*メイン ページ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。

2.  **[Get Started]** (開始) ボタンをクリックします。

    ![](images/AzureLabs-Lab302b-01.png)

3.  サインイン、 *Custom Vision Service*ポータル。

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

4.  求められます初めてログインした後、*サービス利用規約*パネル。 条項に同意する チェック ボックスをクリックします。 をクリックして**同意**します。

    ![](images/AzureLabs-Lab302b-03.png)

5.  条項に同意したことに移動する、*プロジェクト*ポータルのセクション。 をクリックして**新しいプロジェクト**します。

    ![](images/AzureLabs-Lab302b-04.png)

6.  プロジェクトの一部のフィールドを指定するように求められますが、右側にあるタブが表示されます。

    1.  挿入、*名前*プロジェクト用。

    2.  挿入、*説明*プロジェクト用 (*省略可能な*)。

    3.  選択、*リソース グループ*か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

    4. 設定、*プロジェクトの種類*に**分類**
    
    5. 設定、*ドメイン*として**全般**します。

        ![](images/AzureLabs-Lab302b-05.png)

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

7.  をクリックしたら後、**プロジェクトの作成**、Custom Vision Service で、プロジェクトのページにリダイレクトされます。

## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章 – Custom Vision プロジェクトのトレーニング

1 回、Custom Vision ポータルの主な目的はイメージ内の特定のオブジェクトを認識するようにプロジェクトのトレーニングには。 イメージには少なくとも 5 つ (5) 必要がありますが 10 (10) が、アプリケーションを認識したい各オブジェクトで、優先されます。 [(コンピューターのマウスとキーボード) は、このコースで提供されるイメージを使用する](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)します。 

Custom Vision Service プロジェクトのトレーニング。

1.  をクリックして、 **+** 横に**タグ。**

    ![](images/AzureLabs-Lab302b-06.png)

2.  追加、**名前**オブジェクトを認識したいのです。 をクリックして**保存**します。

    ![](images/AzureLabs-Lab302b-07.png)

3.  **タグ**が追加されました (表示するページを再読み込みする必要があります)。 チェックされていない場合は、新しいタグと共にチェック ボックスをクリックします。

    ![](images/AzureLabs-Lab302b-08.png)

4.  をクリックして**の画像の追加**ページの中央にします。

    ![](images/AzureLabs-Lab302b-09.png)

5.  をクリックして**ローカル ファイルを参照**を検索し、最小の中で、アップロードするイメージを選択します。 5 (5)。 これらのイメージはすべてトレーニングは、オブジェクトを含める必要がありますに注意してください。

    > [!NOTE]
    >  一度にアップロードするいくつかのイメージを選択できます。

6.  該当するタグを選択 タブで、イメージを確認できます、**マイ タグ**ボックス。

    ![](images/AzureLabs-Lab302b-10.png)

7.  をクリックして**ファイルをアップロード**します。 ファイル アップロードが開始されます。 アップロードの確認したら、クリックして**完了**します。

    ![](images/AzureLabs-Lab302b-11.png)

8.  新たに作成するのと同じプロセスを繰り返します**タグ**という名前の**キーボード**の適切な写真をアップロードします。 必ず**をオフに***マウス*を表示するために、新しいタグを作成したら、*イメージを追加*ウィンドウ。

9.  両方のタグを設定したら、クリックして**トレーニング**、最初のトレーニングのイテレーションを始めましょう。

    ![](images/AzureLabs-Lab302b-12.png)

10. ビルドされたらという 2 つのボタンを表示できるが**既定**と**予測 URL**します。 をクリックして**既定**でクリックし、最初に、**予測 URL**します。

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > ここから、提供されているエンドポイントの URL どちらに設定されて*イテレーション*が既定としてマークされました。 このため、後で行った場合、新しい*イテレーション*と既定値として更新して、コードを変更する必要はありません。

11. クリックすると*予測 URL*開き、*メモ帳*、コピーして貼り付け、 **URL**と**予測キー**できるように、コードの後半で必要なときに取得します。

    ![](images/AzureLabs-Lab302b-14.png)

12. をクリックして、**歯車**上部にある画面の右。

    ![](images/AzureLabs-Lab302b-15.png)

13. コピー、**トレーニング キー**貼り付けます、*メモ帳*、後で使用します。

    ![](images/AzureLabs-Lab302b-16.png)

14. コピーも、**プロジェクト Id**に貼り付けることも、*メモ帳*ファイルは、後で使用します。

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 - Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。

    ![](images/AzureLabs-Lab302b-17.png)

2.  これで、Unity プロジェクトの名前を指定する必要があります。 挿入**AzureCustomVision します。** 必ず、プロジェクト テンプレートに設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![](images/AzureLabs-Lab302b-18.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して **編集* > *設定** し、新しいウィンドウに移動 **外部ツール** します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![](images/AzureLabs-Lab302b-19.png)

4.  次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。

    ![](images/AzureLabs-Lab302b-20.png)

5.  **ファイル > Build Settings**ことを確認してください。

    1.  **デバイスを対象に**に設定されている**Hololens**

        > イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。
        
    2.  **ビルドの種類**に設定されている**D3D**
    3.  **SDK**に設定されている**インストールされている最新**
    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**
    5.  **ビルドおよび実行**に設定されている**ローカル マシン**
    6.  シーンを保存し、ビルドに追加します。 

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![](images/AzureLabs-Lab302b-21.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![](images/AzureLabs-Lab302b-22.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名:* テキスト フィールドに「 **CustomVisionScene**、[] をクリック**保存**。

            ![](images/AzureLabs-Lab302b-23.png)

            > 注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。 Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。
            
    7.  設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

        ![](images/AzureLabs-Lab302b-24.png)

6.  *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。

7. このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **ランタイム バージョンをスクリプト**する必要があります**試験的 (.NET 4.6 Equivalent)** エディターを再起動する必要があるします。

        2. **バックエンドの scripting**べき **.NET**

        3. **API の互換性レベル**べき **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        1. **InternetClient**

        2.  **Web カメラ**

        3. **マイク**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

    ![](images/AzureLabs-Lab302b-27.png)

8.  戻り*Build Settings* *Unity C\#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。

9.  ビルド設定ウィンドウを閉じます。

10.  シーンとプロジェクトを保存 (**ファイル > SAVE SCENE/ファイル > プロジェクトの保存**)。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>第 4 章 - Unity で Newtonsoft DLL のインポート

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[302b.unitypackage MR-Azure の](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 6 章](#chapter-6---create-the-customvisionanalyser-class)します。

このコースの使用を要求する、 **Newtonsoft**ライブラリで、アセットに DLL として追加することができます。 パッケージを含む[このライブラリは、このリンクからダウンロードできます。](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)します。
プロジェクトに Newtonsoft ライブラリをインポートするには、このコースに付属する Unity パッケージを使用します。

1.  追加、 *.unitypackage* に Unity を使用して、 **資産* > *インポート* *パッケージ* > *カスタム* *パッケージ** メニュー オプション。

2.  **Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。

    ![](images/AzureLabs-Lab302b-28.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、 **Newtonsoft**の下のフォルダー**プラグイン**プロジェクト ビューを選び、 *Newtonsoft.Json プラグイン*します。

    ![](images/AzureLabs-Lab302b-29.png)

5.  *Newtonsoft.Json プラグイン*ように選択すると、 **Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、 をクリックし、**適用**します。 これは、ファイルが正しく構成されていることを確認するだけです。

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > これらのプラグインをマークする Unity エディターでのみ使用することを構成します。 これらのプロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内の異なるセットがあります。

6.  次を開く必要があります、 **WSA**フォルダー内で、 **Newtonsoft**フォルダー。 構成した同じファイルのコピーが表示されます。 ファイルを選択し、インスペクターのことを確認します
    -   **任意のプラットフォーム**は**オフ** 
    -   **のみ** **WSAPlayer**は**チェック**
    -   **処理されないように**は**チェック**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第 5 章 - カメラのセットアップ

1.  [階層] パネルで、選択、 *Main Camera*します。

2.  すべてのコンポーネントを参照してください。 選択すると、ができる、 *Main Camera*で、*インスペクター パネル*します。

    1.  *カメラ*オブジェクトを指定する必要があります**Main Camera** (スペルに注意してください)。

    2.  Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。

    3.  必ず、**変換位置**に設定されている**0, 0, 0**

    4.  設定**フラグをクリア**に**単色**(イマーシブ ヘッドセットの無視) します。

    5.  設定、**バック グラウンド**、カメラの色コンポーネントを**黒、アルファ 0 (16 進コード: #00000000)** (イマーシブ ヘッドセットの無視) します。

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>第 6 章 - CustomVisionAnalyser クラスを作成します。

この時点でコードを記述する準備が整いました。

開始するが、 *CustomVisionAnalyser*クラス。

> [!NOTE]
> 呼び出し、 **Custom Vision Service**に示すコードで行われた以下を使用して作成、 **Custom Vision REST API**します。 これを使用して、実装して (ような画面が独自に実装する方法を理解するために役立ちます) この API を使用する方法が表示されます。 対応しており、Microsoft が提供する、 **Custom Vision Service SDK**をサービスを呼び出すことにも使用できます。 詳細については、次を参照してください。、 [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)記事。

このクラスは、責任を負います。

-   バイト配列としてキャプチャされた最新のイメージを読み込んでいます。

-   バイト配列を Azure に送信する*Custom Vision Service*分析のインスタンス。

-   JSON 文字列としての応答を受信します。

-   応答を逆シリアル化し、その結果を渡して*予測*を*SceneOrganiser*クラスは、応答の表示方法の考慮されます。

このクラスを作成します。

1.  右クリックし、*アセット フォルダー*内にある、*プロジェクト パネル*、順にクリックします**作成 > フォルダー**します。 フォルダーを呼び出す**スクリプト**します。

    ![](images/AzureLabs-Lab302b-33.png)

2.  先ほど作成した、開くフォルダーをダブルクリックします。

3.  フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。 スクリプトの名前*CustomVisionAnalyser*します。

4.  ダブルクリックして、新しい*CustomVisionAnalyser*スクリプト ファイルを開く**Visual Studio**します。

5.  次のように、ファイルの上部にある名前空間を更新します。

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  *CustomVisionAnalyser*クラスで、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 挿入することを確認、**予測キー**に、 **predictionKey**変数、および**予測エンドポイント**に、 **predictionEndpoint**変数。 これらをコピーした*メモ帳*コースで以前。

7.  コードを**Awake()** インスタンス変数を初期化するために追加する必要があります。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  メソッドを削除**Start()** と**Update()** します。

9.  コルーチンを次に、追加 (静的で**GetImageAsByteArray()** 下にあるメソッド)、によってキャプチャされたイメージの分析の結果を取得するが、 *ImageCapture*クラス。

    > [!NOTE]
    > **AnalyseImageCapture**コルーチンへの呼び出しがある、 *SceneOrganiser*クラスを作成することはまだです。 そのため、**は省略します線は、ここではコメント**します。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>7 - 章 CustomVisionObjects クラスを作成します。

クラスの作成はここでは、 *CustomVisionObjects*クラス。

このスクリプトにはへの呼び出しを逆シリアル化およびシリアル化する他のクラスによって使用されるオブジェクト数が含まれています、 *Custom Vision Service*します。

> [!WARNING]
> として、Custom Vision Service が提供するエンドポイントをメモしてを実行することが重要では、次の JSON 構造体がされている設定を使用する[ *Custom Vision 予測 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)します。 別のバージョンがあれば、更新する必要があります、以下の構造体。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す*CustomVisionObjects*します。

2.  ダブルクリックして、新しい**CustomVisionObjects**スクリプト ファイルを開く**Visual Studio**します。

3.  ファイルの先頭には、次の名前空間を追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  削除、 **Start()** と**Update()** 内のメソッド、 *CustomVisionObjects*クラスです。 このクラスを空にする必要がありますするようになりました。

5.  次のクラスを追加**外**、 *CustomVisionObjects*クラス。 これらのオブジェクトを使って、 *Newtonsoft*および応答データを逆シリアル化するライブラリ。

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>8 - 章 VoiceRecognizer クラスを作成します。

このクラスは、ユーザーからの音声入力を認識します。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す*VoiceRecognizer*します。

2.  ダブルクリックして、新しい**VoiceRecognizer**スクリプト ファイルを開く**Visual Studio**します。

3.  上記の次の名前空間を追加、 *VoiceRecognizer*クラス。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  内で、次の変数を追加し、 *VoiceRecognizer*クラス上、 *Start()* メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  追加、 **Awake()** と**Start()** メソッド後者は、ユーザーの設定*キーワード*イメージにタグを関連付けるときに認識されるようにします。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  削除、 **Update()** メソッド。

7.  音声入力が認識されるたびに呼び出される次のハンドラーを追加します。

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

> [!NOTE]
> 心配しないでコードはこれらを修正する、すぐにそれ以上のクラスを提供すると、エラーが表示される可能性があります。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>9 - 章 CustomVisionTrainer クラスを作成します。

このクラスは、一連のトレーニングに web の呼び出しをチェーン、 *Custom Vision Service*します。 各呼び出しは、コードのすぐ上に詳しく説明されます。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す*CustomVisionTrainer*します。

2.  ダブルクリックして、新しい*CustomVisionTrainer*スクリプト ファイルを開く**Visual Studio**します。

3.  上記の次の名前空間を追加、 *CustomVisionTrainer*クラス。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  内で、次の変数を追加し、 *CustomVisionTrainer*クラス上、 **Start()** メソッド。 

    > [!NOTE]
    > ここで使用するトレーニングの URL は用意されている、 *Custom Vision トレーニング 1.2*ドキュメントの構造体であり。 https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 詳細については、次を参照してください。、 [ *v1.2 リファレンスの Custom Vision トレーニング API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)します。

    > [!WARNING]
    > Custom Vision Service を提供するトレーニング モードで使用する JSON 構造体としてエンドポイントをメモしてを実行することが重要になります (内で、 **CustomVisionObjects**クラス) を使用するように設定されている[ *Custom Vision トレーニング v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)します。 別のバージョンがあれば、更新する必要があります、*オブジェクト*構造体。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 追加することを確認、**サービス キー** (トレーニング キー) の値と**プロジェクト Id**値、以前書き留めておいたこれらは、値を[コース (前のポータルから収集された。第 2 章の手順 10 以降)](#chapter-2---training-your-custom-vision-oroject)します。

5.  次の追加**Start()** と**Awake()** メソッド。 これらのメソッドは、初期化時にと呼ばれ、UI を設定する呼び出しを含めます。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  削除、 **Update()** メソッド。 このクラスでは、その必要はありません。

7.  追加、 **RequestTagSelection()** メソッド。 このメソッドは、最初のイメージがキャプチャされ、デバイスに格納されているときに呼び出されるし、提出する準備ができて、 *Custom Vision Service*、トレーニングします。 このメソッドの場合、トレーニング、UI、ユーザーが、キャプチャしたイメージにタグ付けに使用できるキーワードのセットが表示されます。 警告、 *VoiceRecognizer*クラスをユーザーに音声入力のリッスンを開始します。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  追加、 **VerifyTag()** メソッド。 このメソッドによって認識される音声入力が表示されます、 **VoiceRecognizer**クラスし、その有効性を確認し、トレーニング プロセスを開始します。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  追加、 **SubmitImageForTraining()** メソッド。 このメソッドは Custom Vision Service トレーニング プロセスが開始されます。 取得するには、まず、**タグ Id**ユーザーからの検証済みの音声入力に関連付けられているサービスから。 **タグ Id**し、イメージと一緒にアップロードされます。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 追加、 **TrainCustomVisionProject()** メソッド。 イメージは、送信し、タグ付けされていますが、このメソッドが呼び出されます。 サービスと、イメージに送信されたすべての前イメージとトレーニングは新しいイテレーションを作成しますだけアップロードします。 このメソッドは、新しく作成したを設定するメソッドを呼び出す、トレーニングが完了したら、**イテレーション**として**既定**分析を使用しているエンドポイントが最新のトレーニング済み反復処理するようにします。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 追加、 **SetDefaultIteration()** メソッド。 このメソッドは、以前に作成して、トレーニング済みのイテレーションとして設定は*既定*します。 完了すると、このメソッドは、既存のサービスで、前のイテレーションを削除する必要があります。 このコースの作成時は、イテレーションの最大 10 数、サービスで同時に存在できるの制限があります。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 追加、 **DeletePreviousIteration()** メソッド。 このメソッドを検索し、前の既定以外のイテレーションを削除します。

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. このクラスに追加する最後のメソッド、 **GetImageAsByteArray()** メソッド、web の呼び出しでバイト配列にキャプチャされたイメージを変換するために使用します。

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>10 - 章 SceneOrganiser クラスを作成します。

このクラスは。

-   作成、**カーソル**Main Camera にアタッチするオブジェクト。

-   作成、**ラベル**サービスが現実世界のオブジェクトを認識しているときに表示されるオブジェクト。

-   適切なコンポーネントにアタッチすることにより、メイン カメラを設定します。

-   場合に**分析モード**、メイン カメラの位置を基準とした適切なワールド空間における、実行時にラベルを生成、および、Custom Vision Service から受信したデータを表示します。

-   場合に**トレーニング モード**、トレーニング プロセスのさまざまな段階を表示する UI を起動します。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトの名前*SceneOrganiser*します。

2.  ダブルクリックして、新しい*SceneOrganiser*スクリプト ファイルを開く**Visual Studio**します。

3.  1 つの名前空間は必要がありますのみ、上記の他の削除、 *SceneOrganiser*クラス。

    ```csharp
    using UnityEngine;
    ```

4.  内で、次の変数を追加し、 *SceneOrganiser*クラス上、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  削除、 **Start()** と**Update()** メソッド。

6.  変数の右下にある追加の**Awake()** メソッドはクラスを初期化し、シーンを設定します。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  ここで追加、 **CreateCameraCursor()** メソッドを作成して、メイン カメラ、カーソルを配置して、 **CreateLabel()** メソッドで、作成、**分析ラベル**オブジェクト.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 追加、 **SetCameraStatus()** メソッドで、メッセージのテキスト メッシュ、カメラの状態を提供するためのものを処理します。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 追加、 **PlaceAnalysisLabel()** と**SetTagsToLastLabel()** メソッドが生成されをシーンに Custom Vision Service からデータを表示します。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最後に、追加、 **CreateTrainingUI()** メソッドで、アプリケーションがトレーニング モードの場合、トレーニング プロセスの複数のステージを表示する UI が生成されます。 このメソッドは、カメラ状態オブジェクトの作成にも利用されています。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

> [!IMPORTANT]
> 続行する前に開いて、 **CustomVisionAnalyser**クラス内で、 **AnalyseLastImageCaptured()** メソッド、*をコメント解除します*次の行。
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>11 - 章 ImageCapture クラスを作成します。

次のクラスを作成することには、 *ImageCapture*クラス。

このクラスは、責任を負います。

-   HoloLens のカメラを使用して、格納することでイメージのキャプチャ、*アプリ*フォルダー。

-   ユーザーからのタップ ジェスチャを処理します。

-   保守、 *Enum*かどうか、アプリケーションは実行を決定する値*Analysis*モードまたは*トレーニング*モード。

このクラスを作成します。

1.  移動して、**スクリプト**以前に作成したフォルダーです。

2.  フォルダー内を右クリックし、をクリックして**作成 > C\#スクリプト**します。 スクリプトの名前*ImageCapture*します。

3.  ダブルクリックして、新しい**ImageCapture**スクリプト ファイルを開く**Visual Studio**します。

4.  次のように、ファイルの上部にある名前空間に置き換えます。

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  内で、次の変数を追加し、 *ImageCapture*クラス上、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > *Analysis*モード、 **TapHandler**メソッドを開始または写真キャプチャのループを停止するためのスイッチとして機能します。
    >
    > *トレーニング*モードでは、カメラからのイメージがキャプチャされます。
    >
    > カーソルが緑色の場合、カメラは、イメージを使用できることを示します。
    >
    > カーソルが赤の場合は、カメラがビジー状態を意味します。

8.  イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  写真をキャプチャおよび分析する準備ができ次第の呼び出されるハンドラーを追加します。 渡されますが、結果、 *CustomVisionAnalyser*または*CustomVisionTrainer*モードによって、コードに設定します。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

11. これで、すべてのスクリプトが完了したら、Unity エディターでは、戻ってクリックしてアンド ドラッグ、 **SceneOrganiser**クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクトに、*階層パネル*します。

## <a name="chapter-12---before-building"></a>第 12 章 - ビルドの前に

アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。

実行する前にいることを確認します。

- 説明されているすべての設定、[第 2 章](#chapter-2---training-your-custom-vision-project)が正しく設定されています。

- 内のすべてのフィールド、 **Main Camera**インスペクターのパネルが適切に割り当てられます。

- スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。

- 挿入することを確認、**予測キー**に、 **predictionKey**変数。

- 挿入した、**予測エンドポイント**に、 **predictionEndpoint**変数。

- 挿入した、**トレーニング キー**に、 **trainingKey**の変数、 *CustomVisionTrainer*クラス。

- 挿入した、**プロジェクト ID**に、 **projectId**の変数、 *CustomVisionTrainer*クラス。

## <a name="chapter-13---build-and-sideload-your-application"></a>第 13 章 - ビルドおよびサイドロード アプリ

開始する、*ビルド*プロセス。

1.  移動して**ファイル > のビルド設定**します。

2.  ティック**Unity C\#プロジェクト**します。

3.  **[Build]** をクリックします。 Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前**アプリ**します。 使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。

4.  Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。

5.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

HoloLens の展開。

1.  必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。 これには、次の手順を実行します。

    1.  ソックスを着けずに、HoloLens 中を開く、**設定**します。

    2.  移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**

    3.  注、 **IPv4**アドレス。

    4.  次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**

    5.  設定**で開発者モード**します。

2.  新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。

3.  *ソリューション構成*選択**デバッグ**します。

4.  *ソリューション プラットフォーム*、 **x86、リモート コンピューター**します。 挿入を求め、 **IP アドレス**のリモート デバイス (、HoloLens、ここでは、メモしたもの)。

    ![](images/AzureLabs-Lab302b-34.png)

5. 移動して**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。

6. アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。

> [!NOTE]
> イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。 ローカルにデプロイし、machine を使用して、**ビルド**メニュー項目を選択すると*ソリューションの配置*します。 

## <a name="to-use-the-application"></a>アプリケーションを使用します。

アプリの機能との間を切り替える*トレーニング*モードと*予測*モードを更新する必要がある、 **AppMode**変数にある、 **Awake()** 内にあるメソッド、 *ImageCapture*クラス。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
または
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

*トレーニング*モード。

- 見て**マウス**または**キーボード**を使用して、**タップ ジェスチャ**します。

- 次に、テキストは、タグを指定するように求める表示されます。

- どちらか**マウス**または**キーボード**します。


*予測*モード。

- オブジェクトを確認し、使用、**タップ ジェスチャ**します。

- 検出されると、確率が最も高い (これは正規化されます) オブジェクトを提供するテキストが表示されます。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>14 -」の章を評価し、カスタム ビジョン モデルを改善

サービスをより正確なことには、予測に使用するモデルのトレーニングに続行する必要があります。 両方で、新しいアプリケーションを使用して、これは、*トレーニング*と*予測*モード、後者を必要とすると、ポータルでは、この章の内容を参照してください。 何度も、ポータルを見直し、モデルを継続的に向上させるために準備してください。

1. Azure Custom Vision ポータルにもう一度、head し、プロジェクトでは、選択、*予測*(からページの上部中央) タブ。

    ![](images/AzureLabs-Lab302b-35.png)

2. アプリケーションの実行中に、サービスに送信されたすべてのイメージが表示されます。 イメージをポイントする場合は、そのイメージに対して行われた予測の提供は。

    ![](images/AzureLabs-Lab302b-36.png)

3. イメージを開くことのいずれかを選択します。 開いている場合とは、そのイメージの右側に行われた予測が表示されます。 予測が正しいこと、およびサービスのモデルのトレーニングにこのイメージを追加するには、をクリックした場合、*マイ タグ*入力ボックス、およびに関連付けるタグを選択します。 完了したら、クリックして、*を保存して閉じます*右、下にボタンをクリックし、次のイメージを続行します。

    ![](images/AzureLabs-Lab302b-37.png)

4. イメージのグリッドに表示されたら、イメージにタグを追加 (して保存した)、これが表示されますは削除されます。 それらに含まれるタグが付けられた、項目がないと思われる任意のイメージを検索する場合は、(ようイメージがいくつかの) そのイメージに目盛りをクリックし、をクリックして削除することは、できる*削除*グリッド ページの右上隅にします。 次のポップアップで、いずれかをクリックできます*はい、削除*または*いいえ*削除の確認またはキャンセルするか、それぞれをします。 

    ![](images/AzureLabs-Lab302b-38.png)

5. 続行する準備ができたら、緑をクリックします。*トレーニング*右上のボタンをクリックします。 すべてのイメージと指定したようになりましたが (これによりより正確な)、サービス モデルがトレーニングされます。 トレーニングが完了すると作成 をクリックすることを確認して、*既定*、もう一度ボタンをクリックしてように、*予測 URL*は、サービスの最新のイテレーションを使用し続けます。

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>完成した Custom Vision API アプリケーション

これで、現実世界のオブジェクトを認識する、サービス モデルのトレーニングおよび内容は、発生の信頼度を表示する Azure の Custom Vision API を利用している mixed reality アプリを構築します。

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

トレーニング、 **Custom Vision Service**を複数のオブジェクトを認識します。

### <a name="exercise-2"></a>手順 2

学習した内容を展開する方法、として次の演習を行います。

オブジェクトが認識されると、サウンドを再生します。

### <a name="exercise-3"></a>手順 3

API を使用して、アプリの分析は、同じイメージのサービスの再トレーニングに、そのため、サービスをより正確に (予測と同時にトレーニングを行う)。
