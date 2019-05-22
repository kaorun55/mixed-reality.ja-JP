---
title: MR および Azure 305 - 関数およびストレージ
description: このコースでは、複合現実のアプリケーション内で Azure Storage と関数を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、関数、ストレージ、hololens、vr、没入型
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598301"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR と Azure 305:関数とストレージ

![最終的な製品-開始](images/AzureLabs-Lab5-00.png)

このコースでは、作成し、Azure Functions を使用する複合現実のアプリケーション内で、Azure Storage リソースにデータを格納する方法を学びます。

*Azure Functions*できる小規模なコードを実行する開発者の Microsoft サービス '関数'、Azure では、します。 これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。 *Azure Functions* C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。 詳細については、次を参照してください。、 [Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。

*Azure Storage*は、開発者が使用される高可用性、セキュリティで保護された、永続的な拡張性と冗長性保険、データの格納を Microsoft クラウド サービスです。 つまり、Microsoft のすべての保守、および重大な問題を処理します。 詳細については、次を参照してください。、 [Azure Storage の記事](https://docs.microsoft.com/azure/storage/common/storage-introduction)します。

このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。

1.  視線シーンの周囲にユーザーを許可します。
2.  ユーザーが gazes 3D 'button' にあるときに、オブジェクトの生成をトリガーします。
3.  Azure 関数によって生成されたオブジェクトが選択されます。
4.  アプリケーションがオブジェクトの種類を格納するように、各オブジェクトが生成される、 *Azure File*にある*Azure Storage*します。
5.  再度読み込むときに、 *Azure File*データは取得、およびアプリケーションの以前のインスタンスからの起動元のアクションを再生するために使用します。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 できるように、複合現実のアプリケーションを強化するためには、このコースからのナレッジを使用して、ジョブになります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR と Azure 305:関数とストレージ</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。 コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。

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
- Azure リソースを作成するため、Azure アカウントへのサブスクリプション
- Azure のセットアップやデータの取得のためのインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。

## <a name="chapter-1---the-azure-portal"></a>第 1 章 - Azure Portal

使用する、 **Azure ストレージ サービス**、作成および構成する必要があります、**ストレージ アカウント**Azure portal でします。

1.  ログイン、 [Azure Portal](https://portal.azure.com)します。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して*ストレージ アカウント*、 をクリック**Enter**します。

    ![azure storage の検索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

3.  新しいページがの説明を入力、 *Azure Storage アカウント*サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![サービスを作成します。](images/AzureLabs-Lab5-02.png)

4.  クリックすると**作成**:

    1.  挿入、*名前*お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。

    2.  *デプロイ モデル*、 **Resource manager**します。

    3.  *アカウントの種類*、**ストレージ (汎用 v1)** します。

    4.  確認、*場所*(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。

    5.  *レプリケーション*選択**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。

    6.  *パフォーマンス*、**標準**します。

    7.  まま*転送が必須のセキュリティで保護された*として**無効になっている**します。

    8.  選択、*サブスクリプション*します。

    9. 選択、*リソース グループ*か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    10. また、このサービスに適用される条件を理解したことを確認する必要があります。

    11. **[作成]** を選択します。

        ![入力のサービス情報](images/AzureLabs-Lab5-03.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![azure portal で新しい通知](images/AzureLabs-Lab5-04.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。

    ![リソースに移動します。](images/AzureLabs-Lab5-05.png)

8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 実施する、新しい*ストレージ アカウント*サービス インスタンス。

    ![アクセス キー](images/AzureLabs-Lab5-06.png)

9.  をクリックして*アクセス キー*、このクラウド サービスのエンドポイントを表示します。 使用して、*メモ帳*と同様に、後で使用できる、キーの 1 つをコピーするか。 また、*接続文字列*値で使用するため、 *AzureServices*クラスは、後で作成します。

    ![接続文字列をコピー](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第 2 章 – Azure 関数の設定

記述して、 **Azure** **関数**で Azure サービスです。

使用することができます、 **Azure 関数**ほぼ何も行うでの操作とクラシックの関数を使用した、コードの違いは、この関数は、Azure アカウントへのアクセス資格情報を持つ任意のアプリケーションからアクセスできることです。

Azure 関数を作成します。

1.  *Azure Portal*、 をクリックして**新規**左上隅にある検索して*Function App*、 をクリック**Enter**。

    ![function app を作成します。](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

2.  新しいページがの説明を入力、 *Azure Function App*サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![関数アプリの情報](images/AzureLabs-Lab5-09.png)

3.  クリックすると**作成**:

    1.  提供、*アプリ名*します。 アルファベットと数字のみをここで使用することができます (上限または下限のいずれかのケースは許可されています)。

    2.  選択、優先*サブスクリプション*します。

    3. 選択、*リソース グループ*か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    4.  この演習では、次のように選択します。 *Windows*として選択した**OS**します。

    5.  選択*従量課金プラン*の**ホスティング プラン**します。

    6.  確認、*場所*(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。 最適なパフォーマンス、ストレージ アカウントと同じリージョンを選択します。

    7.  *ストレージ*を選択します**既存の**、以前に作成したストレージを検索し、ドロップダウン メニューを使用するとします。

    8.  まま*Application Insights*この演習ではオフです。

        ![入力関数アプリの詳細](images/AzureLabs-Lab5-10.png)

4.  **[作成]** をクリックします。

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![新しい azure portal の通知](images/AzureLabs-Lab5-11.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。 

    ![関数アプリのリソースに移動します。](images/AzureLabs-Lab5-12.png)

8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 実施する、新しい*Function App*サービス インスタンス。

9.  *関数アプリ*ダッシュ ボードで、マウス カーソルを置く*関数*、左側のパネル内に存在し、クリックして、 **+ (正符号 +)** シンボル。

    ![新しい関数を作成します。](images/AzureLabs-Lab5-13.png)

10. 次のページで確認**webhook+api**が選択されていると *、言語の選択*選択**CSharp**、このチュートリアルで使用されている言語があります。 最後に、をクリックして、**この関数を作成**ボタンをクリックします。

    ![web フック csharp を選択します。](images/AzureLabs-Lab5-14.png)

11. コードが表示される、左側のパネル内の関数の一覧で、新しく作成された関数の いない場合 (run.csx) ページの します。

    ![新しい関数を開く](images/AzureLabs-Lab5-15.png)

12. 関数には、次のコードをコピーします。 この関数は、0 と 2 が呼び出されるとの間のランダムな整数を返しますだけです。 既存のコードについて心配ではなく自由に、その上に貼り付けます。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. **[保存]** を選びます。

14. 結果は、次の図のようになります。

15. をクリックして**関数の URL を取得する**メモ、*エンドポイント*が表示されます。 挿入する必要があります、 *AzureServices*このコースの後半で作成するクラス。

    ![関数のエンドポイントを取得します。](images/AzureLabs-Lab5-16.png)

    ![関数のエンドポイントを取得します。](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 - Unity プロジェクトの設定

次のコード例が Mixed Reality での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

設定して、mixed reality イマーシブ ヘッドセットをテストします。

> [!NOTE]
> **いない**このコースのモーションのコント ローラーが必要です。 イマーシブ ヘッドセットの設定をサポートする場合は、次のようにしてください。[記事セットアップ複合現実を参照してください。](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。

1.  Unity を開き、をクリックして**新規**します。

    ![新しい unity プロジェクトを作成します。](images/AzureLabs-Lab5-17.png)

2.  これで、Unity プロジェクト名を指定する必要があります。 挿入**MR_Azure_Functions**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、*場所*に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![新しい unity プロジェクトに名前を付けます](images/AzureLabs-Lab5-18.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して **編集* > *設定** し、新しいウィンドウに移動 **外部ツール** します。 変更 **External Script Editor** に **Visual Studio 2017** します。 閉じる、**設定**ウィンドウ。

    ![スクリプト エディターとして visual studio の設定](images/AzureLabs-Lab5-19.png)

4.  次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![uwp にプラットフォームを切り替える](images/AzureLabs-Lab5-20.png)

5.  移動して**ファイル > Build Settings**ことを確認してください。

    1. **デバイスを対象に**に設定されている**任意のデバイス**します。

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2. **ビルドの種類**に設定されている**D3D**

    3. **SDK**に設定されている**インストールされている最新**

    4. **Visual Studio バージョン**に設定されている**インストールされている最新**

    5. **ビルドおよび実行**に設定されている**ローカル マシン**

    6. シーンを保存し、ビルドに追加します。

        1.  これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![開いているシーンを追加します。](images/AzureLabs-Lab5-21.png)

        2.  新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![シーンのフォルダーを作成します。](images/AzureLabs-Lab5-22.png)

        3.  新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **FunctionsScene**、キーを押します**保存します**。

            ![関数のシーンを保存します。](images/AzureLabs-Lab5-23.png)

6.  設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

    ![関数のシーンを保存します。](images/AzureLabs-Lab5-24.png)

7.  *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。

    ![インスペクターの player の設定](images/AzureLabs-Lab5-25.png)

8.  このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **ランタイム バージョンをスクリプト**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。
        2.  **バックエンドの scripting**べき **.NET**
        3.  **API の互換性レベル**べき **.NET 4.6**

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。
        
        -  **InternetClient**

            ![セットの機能](images/AzureLabs-Lab5-26.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行の設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed RealitySDK**が追加されます。

        ![XR を設定します。](images/AzureLabs-Lab5-27.png)

9.  戻り*Build Settings* *UnityC#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。

    ![ティックの c# プロジェクト](images/AzureLabs-Lab5-28.png)

10.  ビルド設定ウィンドウを閉じます。

11. シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。

## <a name="chapter-4---setup-main-camera"></a>第 4 章 - メイン カメラのセットアップ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)、としてプロジェクトにインポート、[カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)します。 [次へ] の章から Dll が含まれます。 インポートの後から引き続き[第 7 章](#chapter-7---create-the-azureservices-class)します。 

1.  *階層パネル*、という名前のオブジェクトが表示されます**Main Camera**、「内部」アプリケーションが表示されたら、このオブジェクトは、"head"の観点を表します。

2.  選択する前にある Unity ダッシュ ボードで、**メイン カメラの GameObject**します。 表示になります、*インスペクター パネル*(一般にダッシュ ボードで、右側にあります) をさまざまなコンポーネントが表示されます*GameObject*で*変換*後に、上部にある*カメラ*、およびその他のコンポーネント。 これが正しく配置されているため、メイン カメラの変換をリセットする必要があります。

3.  これを行うには、選択、**歯車**カメラの横にあるアイコン*変換*コンポーネント、および選択**リセット**。

    ![変換をリセットします。](images/AzureLabs-Lab5-29.png)

4.  更新し、**変換**のようにコンポーネント。

    |         |    変換の位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 変換の回転 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 変換のスケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![セットのカメラの変換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第 5 章 - Unity シーンの設定

1.  空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**平面**します。

    ![新しい面を作成します。](images/AzureLabs-Lab5-31.png)

2.  **平面**オブジェクトの選択されている、次のパラメーターを変更、*インスペクター パネル*:

    |       | 変換の位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 変換のスケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![平面の位置を設定してスケール](images/AzureLabs-Lab5-32.png)

    ![平面のシーン ビュー](images/AzureLabs-Lab5-33.png)

3.  空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**キューブ**します。

    1.  キューブの名前を変更**GazeButton** (選択されているキューブを押して 'F2')。

    2.  次のパラメーターを変更、*インスペクター パネル*:

        |       | 変換の位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![セットの視線入力ボタンの変換](images/AzureLabs-Lab5-34.png)

        ![視線ボタン シーン ビュー](images/AzureLabs-Lab5-35.png)

    3.  をクリックして、**タグ**ドロップダウン ボタンをクリックします**タグを追加**を開く、*レイヤー ペイン (&)、タグ*します。

        ![新しいタグを追加します。](images/AzureLabs-Lab5-36.png)

        ![プラス記号を選択します](images/AzureLabs-Lab5-37.png)

    4.  選択、 **+ (正符号 +)** ボタン、し、*新しいタグ名*フィールドに、入力**GazeButton**、キーを押します**保存**。

        ![新しいタグの名前](images/AzureLabs-Lab5-38.png)

    5.  をクリックして、 **GazeButton**オブジェクト、*階層パネル*、し、*インスペクター パネル*、割り当て、新しく作成された**GazeButton**タグ。

        ![視線入力ボタンをクリックして新しいタグを割り当てる](images/AzureLabs-Lab5-39.png)

4.  右クリックし、 **GazeButton**オブジェクトで、*階層パネル*、追加、**空の GameObject** (として追加されます、*子*オブジェクトの場合)。

5.  新しいオブジェクトを選択し、名前変更**ShapeSpawnPoint**します。

    1.  次のパラメーターを変更、*インスペクター パネル*:

        |       | 変換の位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![図形の生成のポイントの変換を更新します。](images/AzureLabs-Lab5-40.png)

        ![図形の起動ポイント シーン ビュー](images/AzureLabs-Lab5-41.png)

6.  次に作成、 **3D テキスト**Azure サービスの状態に関するフィードバックを提供するオブジェクト。

    右クリックして、 **GazeButton**階層でもう一度 パネルを追加、 **3D オブジェクト > 3D テキスト**オブジェクトとして、*子*します。

    ![新しい 3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab5-42.png)

7.  名前の変更、 **3D テキスト**オブジェクトを**AzureStatusText**します。

8.  変更、 **AzureStatusText**オブジェクトの次のように変換します。

    |       | 変換の位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 変換のスケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > センターをオフにこれは修正される場合に表示される場合も心配はありません、以下のテキストのメッシュ コンポーネントが更新されます。

9.  変更、**テキスト メッシュ**と一致するコンポーネントの下。

    ![テキストの設定のメッシュ コンポーネント](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > ここで選択した色は、16 進数の色を示します。**000000FF**、ただし、自由に独自の選択、それを読み取ることが確認します。

10. パネルの階層構造は、次のようになります。

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab5-43b.png)

10. シーンは、次のようになります。

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第 6 章 - Unity 用の Azure Storage のインポート

Unity の Azure ストレージを使用する (それ自体を活用して、.Net SDK for Azure)。 詳細について、 [Unity 記事用の Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。

インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。 バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。

独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[GitHub からの '.unitypackage'](https://aka.ms/azstorage-unitysdk)します。 次に、次の操作を行います。

1.  追加、 **.unitypackage** Unity を使用して、ファイル、**資産 > パッケージのインポート > カスタム パッケージ**メニュー オプション。

2.   **Unity パッケージのインポート** ポップアップ、選択できることの下のすべてのボックス **プラグイン* > *ストレージ。 このコースの必要がないと、その他のすべてをオフにします。

    ![パッケージへのインポートします。](images/AzureLabs-Lab5-45.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、*ストレージ*の下のフォルダー*プラグイン*、プロジェクトのビューを選び、次のプラグイン*のみ*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![任意のプラットフォームをオフにします。](images/AzureLabs-Lab5-46.png)

5.  *これら特定のプラグイン*選択すると、**をオフに** *Any プラットフォーム*と**をオフに** *WSAPlayer*クリックして**適用**します。

    ![プラットフォームの dll を適用します。](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Unity エディターでのみ使用するこれらの特定のプラグインをマークするされます。 WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。

6.  *ストレージ*プラグイン フォルダーのみを選択します。

    -   Microsoft.Data.Services.Client

        ![dll のセットを処理しません。](images/AzureLabs-Lab5-48.png)

7.  チェック、**しないプロセス**ボックス*プラットフォームの設定* をクリック**適用**します。

    ![処理は適用されません。](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 私たちはマークするこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。 このプラグインは処理されていない場合でも機能します。

## <a name="chapter-7---create-the-azureservices-class"></a>7 -」の章の azure サービス クラスを作成します。

最初のクラスを作成するには、 *AzureServices*クラス。

*AzureServices*を担当するクラス。

-   Azure アカウントの資格情報を格納します。

-   Azure アプリ関数を呼び出しています。

-   アップロードと Azure のクラウド ストレージにデータ ファイルのダウンロード。

このクラスを作成します。

1.  右クリックし、*資産*フォルダーで、[プロジェクト] パネルにある**作成 > フォルダー**します。 フォルダーの名前**スクリプト**します。

    ![新しいフォルダーを作成します。](images/AzureLabs-Lab5-50.png)

    ![フォルダーのスクリプトを呼び出す](images/AzureLabs-Lab5-51.png)

2.  先ほど作成した、開くフォルダーをダブルクリックします。

3.  フォルダー内を右クリックして**作成 >C#スクリプト**します。 スクリプトを呼び出す*AzureServices*します。

4.  新しいをダブルクリックします。 *AzureServices*クラス ファイルを開く*Visual Studio*します。

5.  先頭に次の名前空間を追加、 *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  内で、次のインスペクター フィールドを追加、 *AzureServices*クラス。

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  内の次のメンバー変数を追加し、 *AzureServices*クラス。

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 置換するかどうかを確認、*エンドポイント*と*接続文字列*値と、Azure storage からの値が、Azure ポータルで確認

8.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。 これらのメソッドが、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > コードの入力は*CallAzureFunctionForNextShape()* で、[将来章](#chapter-10---completing-the-AzureServices-class)します。

9.  削除、 *Update()* メソッドのため、このクラスは使用されません。

10. Visual Studio で、変更を保存し、Unity に戻ります。

11. クリックしてドラッグし、 *AzureServices* Scripts フォルダーからクラスの Main Camera オブジェクトを*階層パネル*します。

12. メイン カメラを選択し、取得、 **AzureStatusText**から下に子オブジェクト、 **GazeButton**オブジェクト、および配置内で、 **AzureStatusText**参照先フィールドに、*インスペクター*への参照を提供する、 *AzureServices*スクリプト。

    ![テキストの参照先の azure の状態を割り当てる](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>8 - 章 ShapeFactory クラスを作成します。

次のスクリプトを作成するには、 *ShapeFactory*クラス。 このクラスの役割は、要求されたときに、新しい図形を作成しで作成した図形の履歴を保持する*図形履歴リスト*します。 図形が作成されるたびに、*図形履歴リスト*で更新、 *AzureService*クラス、およびに格納し、 *Azure Storage*します。 アプリケーションの起動時、格納されているファイルが見つかった場合、 *Azure Storage*、*図形履歴リスト*が取得され、再生で、 **3D テキスト**オブジェクトを提供します。生成された図形がストレージから、または新しいかどうか。

このクラスを作成します。

1.  移動して、**スクリプト**以前に作成したフォルダーです。

2.  フォルダー内を右クリックして**作成 >C#スクリプト**します。 スクリプトを呼び出す*ShapeFactory*します。

3.  新しいをダブルクリックします。 *ShapeFactory*スクリプト ファイルを開く*Visual Studio*します。

4.  確認、 *ShapeFactory*クラスには、次の名前空間が含まれています。

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  次に示す変数を追加、 *ShapeFactory*クラスし、置換、 *Start()* と*Awake()* と次の関数。

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape()* メソッドに基づいて、指定したプリミティブ図形は生成*整数*パラメーター。 ブール型パラメーターは、現在作成されている図形は、ストレージからかどうかを指定するために使用または新しいです。 次のコードを配置、 *ShapeFactory*クラスは、前のメソッドの下。

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Visual Studio で Unity に戻る前に変更を保存することを確認します。

8.  戻る Unity エディターで、をクリックし、ドラッグ、 *ShapeFactory*クラスから、**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*.

9. 選択したメイン カメラで表示されます、 *ShapeFactory*スクリプト コンポーネントが不足している、 *Spawn ポイント*参照。 これを修正するには、ドラッグ、 **ShapeSpawnPoint**オブジェクトから、*階層パネル*を**Spawn ポイント**参照先。

    ![セット図形工場出荷時の参照先](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>9 - 章視線の先クラスを作成します。

最後のスクリプトを作成する必要がありますが、*視線*クラス。

作成するため、このクラスは、 **Raycast**ユーザーを見て、どのオブジェクトを検出するために、メイン カメラから転送投影されます。 Raycast の必要があります、ユーザーが見る場合を識別するためにここで、 **GazeButton**シーン内のオブジェクトし、動作をトリガーします。

このクラスを作成します。

1.  移動して、**スクリプト**以前に作成したフォルダーです。

2.  プロジェクト パネルで、右クリックして**作成 >C#スクリプト**します。 スクリプトを呼び出す*視線*します。

3.  新しいをダブルクリックします。*視線*スクリプト ファイルを開く*Visual Studio。*

4.  次の名前空間が、スクリプトの先頭に含まれることを確認するには。

    ```csharp
        using UnityEngine;
    ```

5.  内で、次の変数を追加し、*視線*クラス。

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> これらの変数の一部では編集できなく、*エディター*します。

6.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  と共に開始位置でカーソル オブジェクトを作成する次のコードを追加、 *Update()* GazeEnabled ブール値を切り替えると、Raycast メソッドを実行するメソッド。

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 次を追加、 *UpdateRaycast()* メソッドでは、プロジェクト、Raycast され、ヒットのターゲットを検出します。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最後に、追加、 *ResetFocusedObject()* メソッドで、GazeButton オブジェクトの現在色、かどうか、新しい図形を作成しているかどうかを示すとオフが切り替わります。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Visual Studio で Unity に戻る前に、変更を保存します。

11.  クリックしてドラッグし、*視線*Scripts フォルダーからのクラス、 **Main Camera**オブジェクト、*階層パネル*します。

## <a name="chapter-10---completing-the-azureservices-class"></a>第 10 章 – AzureServices クラスの完了

場所にその他のスクリプトを使用して行うことが今すぐ*完了*、 *AzureServices*クラス。 これは、によって実現されます。

1.  という名前の新しいメソッドを追加する*CreateCloudIdentityAsync()* Azure と通信するために必要な認証の変数を設定します。

    > このメソッドは図形の一覧を含んでいる以前に格納されているファイルが存在することも確認します。
    >
    > **ファイルが見つかった場合**、ユーザーを無効にするには、*視線*に格納されている、図形のパターンに従って、図形の作成をトリガーし、 **Azure Storage ファイル**します。 ユーザーが、これとして表示、**テキスト メッシュ**表示が提供されます 'Storage' または図形の送信元によって ' New' をします。
    >
    > **ファイルが見つからない場合**が有効になります、*視線*、見る際に図形を作成するユーザーを有効にすると、 **GazeButton**シーン内のオブジェクト。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  次のコード スニペットは、内から、 *Start()* メソッドは、呼び出しができる、 *CreateCloudIdentityAsync()* メソッド。 現在経由でコピーする自由*Start()* メソッドの下。

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  メソッドのコードを入力*CallAzureFunctionForNextShape()* します。 使用前に作成した*Azure Function App*図形のインデックスを要求します。 このメソッドが図形を送信する新しい図形を受信すると、 *ShapeFactory*シーン内に新しい図形を作成するクラス。 完了の本文を次のコードを使用して*CallAzureFunctionForNextShape()* します。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  保存することで、図形の履歴リストに格納する整数を連結して文字列を作成するメソッドを追加、 *Azure Storage ファイル*します。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  あるファイルに格納されているテキストを取得するメソッドを追加、 *Azure Storage ファイル*と*逆シリアル化*一覧にします。

6.  このプロセスが完了すると、メソッドを再度有効に、視線の先、ユーザーが図形をシーンに追加できるようにします。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Visual Studio で Unity に戻る前に、変更を保存します。

## <a name="chapter-11---build-the-uwp-solution"></a>第 11 章 – UWP ソリューションのビルド

ビルド プロセスを開始します。

1.  移動して**ファイル > のビルド設定**します。

    ![アプリをビルドします](images/AzureLabs-Lab5-54.png)

2.  **[Build]** をクリックします。 Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前*アプリ*します。 使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。

3.  Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。

4.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-12---deploying-your-application"></a>第 12 章 - アプリケーションのデプロイ

アプリケーションを配置します。

1.  移動し、*アプリ*で作成されたフォルダー、[最後の章](#chapter-11---build-the-uwp-solution)します。 アプリ名に '.sln' の拡張機能は、する必要がありますをダブルクリックすると、ファイルが表示されます、内で開くために*Visual Studio*します。

2.  **ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。

3.  **ソリューション構成**選択**デバッグ**します。

    > Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。 ただし、次の操作も必要があります。
    > - 把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。 
    > - 確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。

    ![ソリューションを配置します。](images/AzureLabs-Lab5-55.png)

4.  移動して、**ビルド**メニューをクリックします**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。

5.  アプリが起動され、テストする準備が、インストールされているアプリの一覧に表示されます。

## <a name="your-finished-azure-functions-and-storage-application"></a>完成した、Azure Functions と Storage アプリケーション

これで、Azure Functions と Azure Storage の両方のサービスを利用している mixed reality アプリを構築します。 アプリは格納されたデータは、上に描画し、そのデータに基づいてアクションを提供することになります。

![最終的な製品-終了](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

ポイントとから作成されたオブジェクトの状態を生成するレコードは、2 つ目の生成を作成します。 データ ファイルを読み込むときに、もともと作成された場所から子の図形を再生します。

### <a name="exercise-2"></a>手順 2

毎回を再び開くにせずに、アプリを再起動する方法を作成します。 **シーンを読み込む**は適切なスポットを開始します。 格納リストをクリアする方法を作成した後、 *Azure Storage*、アプリから簡単にリセットできるようにします。 
