---
title: 様、Azure の 302 - Computer vision
description: このコースでは、複合現実のアプリケーションで Azure の Computer Vision を使用して、指定されたイメージ内のビジュアルのコンテンツを認識する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、コンピューター ビジョン、没入型、hololens、vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597891"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR と Azure 302:コンピューター ビジョン

このコースでは複合現実のアプリケーションで Azure の Computer Vision の機能を使用して、指定されたイメージ内のビジュアルのコンテンツを認識する方法についてはします。

認識の結果がわかりやすいタグとして表示されます。 このサービスは、機械学習モデルをトレーニングすることがなく使用できます。 実装では、機械学習モデルをトレーニングする必要がある場合は、次を参照してください。 [MR と Azure 302b](mr-azure-302b.md)します。

![ラボの結果](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision には、すべてクラウドから高度なアルゴリズムを使用してイメージ処理と (戻り値情報の場合) を使用した分析を開発者に提供するように設計 Api のセットです。 開発者は、イメージまたは画像の URL をアップロードし、Microsoft Computer Vision API アルゴリズムがビジュアルのコンテンツを分析し、情報を返すことができる、ユーザーを選択した入力に基づいて人の顔 (を検出を含む、型と、イメージの品質を識別します。それぞれの座標を返す)、およびタグ付け、または画像を分類します。 詳細については、次を参照してください。、 [Azure Computer Vision API ページ](https://azure.microsoft.com/services/cognitive-services/computer-vision/)します。

このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。

1.  タップ ジェスチャを使用して、HoloLens のカメラはイメージをキャプチャします。
2.  イメージは、Azure コンピューター ビジョンの API サービスに送信されます。 
3.  認識されるオブジェクトは、Unity シーンに配置されている単純な UI グループに表示されます。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 302:コンピューター ビジョン</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。 (VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。 コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。

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
- (イマーシブ ヘッドセット開発) は、PC に接続されているカメラ
- Azure のセットアップおよび Computer Vision API 取得するためのインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1--the-azure-portal"></a>第 1 章 – Azure Portal

使用する、 *Computer Vision API*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  最初に、ログイン、 [Azure Portal](https://portal.azure.com)します。 

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して*Computer Vision API*、 をクリック**Enter**します。

    ![Azure で新しいリソースを作成します。](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。
 
3.  新しいページがの説明を入力、 *Computer Vision API*サービス。 このページの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![コンピューター ビジョンの api サービスについて](images/AzureLabs-Lab2-01.png)
 
4.  クリックすると**作成**:

    1. 必要な挿入**名前**このサービス インスタンス。
    2. 選択、**サブスクリプション**します。
    3. 選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Computer Vision API*サービス、(F0 という名前)、free レベルを使用可能にする必要があります。
    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. (新しいリソース グループを作成する) 場合は、リソース グループの場所を決定します。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。

    6. また、このサービスに適用される条件を理解したことを確認する必要があります。
    7. [作成] をクリックします。

        ![サービスの作成情報](images/AzureLabs-Lab2-02.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。
6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![新しいサービスの新しい通知を参照してください。](images/AzureLabs-Lab2-03.png) 
 
7.  新しいサービス インスタンスを探索する通知をクリックします。 

    ![リソースに移動 ボタンを選択します。](images/AzureLabs-Lab2-04.png)
 
8. をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 新しい Computer Vision API サービスのインスタンスに表示されます。 

    ![Computer Vision API の新しいサービス](images/AzureLabs-Lab2-05.png)
 
9.  このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。
10. *クイック スタート* ページの*Computer Vision API*サービスは、最初のステップに移動し、*キーを取得する*、 をクリック**キー** (これを行うキー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。 これが明らかに、サービス*キー*します。
11. このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。 

12. 戻り、*クイック スタート*ページ、およびそこから、エンドポイントを取得します。 自分、お住まいの地域に応じて異なる可能性がありますに注意してください (これは、後で、コードに、変更を行う必要があります)。 後で使用するには、このエンドポイントのコピーを作成するには。

    ![Computer Vision API の新しいサービス](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > さまざまなエンドポイントをチェックする[ここ](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)します。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章 – Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab2-06.png)

2.  これで、Unity プロジェクト名を指定する必要があります。 挿入**MR_ComputerVision**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab2-07.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab2-08.png)

4.  次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab2-10.png)

5.  **ファイル > Build Settings**ことを確認してください。

    1. **デバイスを対象に**に設定されている**HoloLens**

        > イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。

    2. **ビルドの種類**に設定されている**D3D**
    3. **SDK**に設定されている**インストールされている最新**
    4. **Visual Studio バージョン**に設定されている**インストールされている最新**
    5. **ビルドおよび実行**に設定されている**ローカル マシン**
    6. シーンを保存し、ビルドに追加します。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。
        
            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab2-11.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab2-12.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_ComputerVisionScene**、順にクリックします**保存**.

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab2-13.png)

            > 注意してください、内の Unity シーンを保存する必要があります、*資産*フォルダー、Unity プロジェクトに関連付けられている必要があります。 Unity プロジェクトの構造の一般的な方法は、シーン フォルダー (およびその他の同様のフォルダー) を作成します。

    7. 設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

6. *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab2-14.png)

7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1. **ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。
        2. **バックエンドの scripting**べき **.NET**
        3. **API の互換性レベル**べき **.NET 4.6**

            ![その他の設定を更新します。](images/AzureLabs-Lab2-15.png)
      
    2. 内で、**発行の設定**] タブの [**機能**、確認してください。

        1. **InternetClient**
        2. **Web カメラ**

            ![発行の設定を更新しています。](images/AzureLabs-Lab2-16.png)

    3. パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![X の R の設定を更新します。](images/AzureLabs-Lab2-17.png)

8.  戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。 
9.  ビルド設定ウィンドウを閉じます。
10. シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 – メイン カメラのセットアップ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)、としてプロジェクトにインポート、[カスタム パッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-resultslabel-class)します。

1.  *階層パネル*を選択、 **Main Camera**します。 
2.  すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。

    1. **Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。
    2. Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。
    3. 必ず、**変換位置**に設定されている**0, 0, 0**
    4. 設定**フラグをクリア**に**単色**(イマーシブ ヘッドセットの無視) します。
    5. 設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (16 進コード: #00000000)** (イマーシブ ヘッドセットの無視) します。

        ![カメラのコンポーネントを更新します。](images/AzureLabs-Lab2-18.png)
 
3.  次に接続されている単純な"Cursor"オブジェクトを作成する必要が、 **Main Camera**、画像分析を配置するのに役立つ出力は、アプリケーションが実行されています。 このカーソルでは、カメラのフォーカスの中心点を決定します。

カーソルを作成します。

1.  *階層パネル*を右クリックし、 **Main Camera**します。 [ **3D オブジェクト**、] をクリックして**球**します。

    ![カーソル オブジェクトを選択します。](images/AzureLabs-Lab2-19.png)
 
2.  名前の変更、**球**に**カーソル**(カーソル オブジェクトをダブルクリックまたはオブジェクトを選択した 'F2' キーボード ボタンを押す) の子であるかどうかを確認して、 **Main Camera**.

3.  *階層パネル*、左クリックしてで、**カーソル**します。 カーソルが選択されている、調整では、次の変数、*インスペクター パネル*:

    1. 設定、*位置を変換*に**0, 0, 5**
    2. 設定、*スケール*に**0.02、0.02、0.02**

        ![変換の位置とスケールを更新します。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第 4 章 – ラベルのシステムのセットアップ

HoloLens のカメラでは、イメージをキャプチャした、そのイメージに送信する、 *Azure Computer Vision API*分析のためのサービス インスタンス。 

分析の結果と呼ばれる、認識されているオブジェクトのリストが返されます**タグ**します。 

(としてワールド空間における 3D テキスト)、写真の撮影場所にこれらのタグを表示するラベルは使用します。

次の手順では説明を設定する方法、**ラベル**オブジェクト。

1.  階層のパネル (場所がこの時点で関係ありませんが)、任意の場所を右クリックして**3D オブジェクト**、追加、 **3D テキスト**します。 名前を付けます**LabelText**します。

    ![3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab2-21.png)
 
2.  *階層パネル*、左クリックしてで、 **LabelText**します。 **LabelText**で次の変数を選択すると、調整、*インスペクター パネル*:

    1. 設定、**位置**に**0,0,0**
    2. 設定、**スケール**に**0.01、0.01、0.01**
    3. コンポーネントで**テキスト メッシュ**:
    4. 内のすべてのテキストを置き換える**テキスト**、with「...」        
    5. 設定、**アンカー**に**中央**
    6. 設定、**配置**に**センター**
    7. 設定、 **タブ サイズ**に**4**
    8. 設定、**フォント サイズ**に**50**
    9. 設定、**色**に **#FFFFFFFF**

    ![テキストのコンポーネント](images/AzureLabs-Lab2-21-5.png)

3.  ドラッグ、 **LabelText**から、*階層パネル*に、*アセット フォルダー*内での*プロジェクト パネル*します。 これは、ように、 **LabelText**プレハブ、コードでその it をインスタンス化できるようにします。

    ![LabelText オブジェクトのプレハブを作成します。](images/AzureLabs-Lab2-22.png)
 
4.  削除する必要があります、 **LabelText**から、*階層パネル*、開くシーンでは表示されません。 プレハブを Assets フォルダーから個々 のインスタンスで呼び出すが、これは現在、シーン内に収まる必要はありません。 
5.  最終的なオブジェクトの構造、*階層パネル*次の図に示すようになります。

    ![階層のパネルの最終的な構造体。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第 5 章 – ResultsLabel クラスを作成します。

最初のスクリプトを作成する必要がありますが、 *ResultsLabel*クラスは、次の原因となっています。 

- カメラの位置を基準とした、適切なワールド空間で、ラベルを作成します。
- イメージれたからタグを表示します。

このクラスを作成します。 

1.  右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。 フォルダーの名前**スクリプト**します。 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab2-24.png)

2.  **スクリプト**フォルダーの作成、アイコンをダブルクリックして開きます。 そのフォルダーを右クリックし、内**作成 >** し**C#スクリプト**します。 スクリプトの名前*ResultsLabel*します。 

3.  新しいをダブルクリックします。 *ResultsLabel*スクリプト ファイルを開く**Visual Studio**します。

4.  クラス内で次のコードを挿入、 *ResultsLabel*クラス。

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。
7.  戻り、 *Unity エディター* をクリックし、ドラッグ、 *ResultsLabel*クラスから、**スクリプト**フォルダーを**Main Camera** 内のオブジェクト*階層パネル*します。
8.  をクリックして、 **Main Camera**を見て、*インスペクター パネル*します。

カメラにドラッグしたスクリプトからが 2 つのフィールドが表示されます。**カーソル**と**Prefab ラベル**します。

9.  呼ばれるオブジェクトをドラッグして**カーソル**から、*階層パネル*という名前のスロットに**カーソル**、次の図に示すようにします。
10. 呼ばれるオブジェクトをドラッグして**LabelText**から、 *Assets フォルダー*で、*プロジェクト パネル*という名前のスロットに**ラベル Prefab**ように、次の図。 

    ![Unity 内で参照のターゲットを設定します。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第 6 章 – ImageCapture クラスを作成します。

次のクラスを作成することには、 *ImageCapture*クラス。 このクラスは、責任を負います。

-   HoloLens のカメラを使用して、アプリ フォルダーに格納することとイメージをキャプチャします。
-   ユーザーからのタップ ジェスチャをキャプチャします。

このクラスを作成します。 

1.  移動して、**スクリプト**以前に作成したフォルダーです。 
2.  フォルダー内を右クリックして**作成 >C#スクリプト**します。 スクリプトを呼び出す*ImageCapture*します。 
3.  新しいをダブルクリックします。 *ImageCapture*スクリプト ファイルを開く**Visual Studio**します。
4.  ファイルの先頭には、次の名前空間を追加します。

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  内で、次の変数を追加し、 *ImageCapture*クラス上、 *Start()* メソッド。

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount**変数で、ユーザーからキャプチャされたタップ ジェスチャの数を格納します。 この番号は、キャプチャしたイメージの名前付けで使用されます。

6.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。 これらが、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler()* メソッドは、ユーザーからキャプチャされたタップ数をインクリメントし、現在のカーソル位置を使用して、新しいラベルを配置する場所を決定します。

このメソッドを呼び出して、 *ExecuteImageCaptureAndAnalysis()* メソッドをこのアプリケーションのコア機能を開始します。

8.  イメージをキャプチャして保存すると、以下のハンドラーが呼び出されます。 結果が渡されるプロセスが成功した場合、 *VisionManager* (まだ作成としています) を分析します。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  次に、イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール パネル*します。 これは、コードを参照しているため、 *VisionManager*クラスは次の章で作成されます。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第 7 章 – Azure と画像分析への呼び出し

最後のスクリプトを作成する必要がありますが、 *VisionManager*クラス。 

このクラスは、責任を負います。

-   バイト配列としてキャプチャされた最新のイメージを読み込んでいます。
-   送信するバイト配列、 *Azure Computer Vision API*分析のためのサービス インスタンス。
-   JSON 文字列としての応答を受信します。
-   応答を逆シリアル化し、結果として得られるタグを渡す、 *ResultsLabel*クラス。
 
このクラスを作成します。

1.  ダブルクリック、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前*VisionManager*します。 
3.  Visual Studio で開くことに新しいスクリプトをダブルクリックします。
4.  上部にある、次と同じである名前空間の更新、 *VisionManager*クラス。

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  スクリプトの上部にある*内*、 *VisionManager*クラス (上、 *Start()* メソッド)、2 つ作成する必要があります*クラス*ですAzure からの逆シリアル化された JSON 応答を表します。

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData*と*AnalysedObject*クラスが必要です、 *[System.Serializable]* Unity で逆シリアル化できる宣言の前に追加された属性ライブラリ。

6.  VisionManager クラスでは、次の変数を追加する必要があります。

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 挿入することを確認、**認証キー**に、 **authorizationKey**変数。 メモは、**認証キー**のこのコースでは、先頭に[第 1 章](#chapter-1--the-azure-portal)します。

    > [!WARNING] 
    > **VisionAnalysisEndpoint**変数は、この例で指定されている異なる場合があります。 **西部、米国**厳密に言うと、米国西部リージョンに作成されたサービス インスタンスにします。 これを更新、[エンドポイント URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。 ここではその例をいくつかのようになります。
    > - 西ヨーロッパ: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 東南アジア。 `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - オーストラリア東部: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  今すぐ、Awake のコードは、追加する必要があります。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  によってキャプチャされたイメージの分析の結果を取得する (ストリームの静的メソッドで下にある)、コルーチンを次に、追加、 *ImageCapture*クラス。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。
10. 戻る Unity エディターで、をクリックし、ドラッグ、 *VisionManager*と*ImageCapture*クラスを**スクリプト**フォルダーを**Main Camera**オブジェクト、*階層パネル*します。 

## <a name="chapter-8--before-building"></a>第 8 章: ビルドする前に

アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。
実行する前にいることを確認します。

-   説明されているすべての設定[第 2 章](#chapter-2--set-up-the-unity-project)が正しく設定されています。 
-   関連付けられているすべてのスクリプト、 **Main Camera**オブジェクト。 
-   内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。
-   挿入することを確認、**認証キー**に、 **authorizationKey**変数。
-   エンドポイントもチェックすることを確認、 *VisionManager*スクリプト、およびに合わせて配置 *、* リージョン (このドキュメントでは*西-ご*既定)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>9 – 章ビルド UWP ソリューションおよびサイドロード アプリケーション
このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します*ビルド設定* - **ファイル > の設定を作成しています.**
2.  *Build Settings*ウィンドウで、をクリックして**ビルド**します。

    ![Unity からのアプリの構築](images/AzureLabs-Lab2-26.png)

3.  まだ行っていない場合、ティック**UnityC#プロジェクト**します。
4.  **[Build]** をクリックします。 Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前*アプリ*します。 使用し、*アプリ*フォルダーを選択すると、キーを押して**フォルダーの選択**します。 
5.  Unity にプロジェクトをビルドを開始、*アプリ*フォルダー。 
6.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、*ファイル エクスプ ローラー*ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-10--deploy-to-hololens"></a>HoloLens に章 – 10 を展開します。

HoloLens の展開。

1.  必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。 これには、次の手順を実行します。

    1. ソックスを着けずに、HoloLens 中を開く、**設定**します。
    2. 移動して**ネットワークとインターネット > Wi-fi > 詳細オプション**
    3. 注、 **IPv4**アドレス。
    4. 次に移動します**設定**、し**更新とセキュリティ > 開発者向け** 
    5. 開発者モードを設定します。

2.  新しい Unity ビルドに移動します (、*アプリ*フォルダー) とソリューション ファイルを開くと*Visual Studio*します。
3.  ソリューション構成の選択で**デバッグ**します。
4.  ソリューション プラットフォーム で選択**x86**、**リモート マシン**します。 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab2-27.png)
 
5.  移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。
6.  アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。

> [!NOTE]
> イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。 ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。 

## <a name="your-finished-computer-vision-api-application"></a>完成した Computer Vision API アプリケーション

これで、現実世界のオブジェクトを認識し、内容は、発生の信頼度を表示する Azure の Computer Vision API を利用している mixed reality アプリを構築します。

![ラボの結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

使用したのと同様、*タグ*パラメーター (内からわかるように、*エンドポイント*内で使用される、 *VisionManager*)、その他の情報を検出するためにアプリを拡張; を見てその他のパラメーターへのアクセスがある[ここ](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)します。

### <a name="exercise-2"></a>手順 2

おそらく、番号を非表示より会話で読みやすい方法で返される Azure のデータを表示します。 いなくても、ボットは、ユーザーに話す可能性があります。
