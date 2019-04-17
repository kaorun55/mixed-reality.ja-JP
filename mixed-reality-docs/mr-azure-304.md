---
title: MR と Azure 304 - 顔認識
description: このコースでは、複合現実のアプリケーション内で Azure の顔認識機能を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure では、顔認識、hololens、没入型、vr の実際に、アカデミー、unity、チュートリアル、api を混在
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603810"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR と Azure 304:顔認識

![このコースを完了するの結果](images/AzureLabs-Lab4-00.png)

このコースでは Microsoft Face API を使用した Azure Cognitive Services を使用して複合現実のアプリケーションに顔認識機能を追加する方法についてはします。

*Azure の Face API*は、開発者はすべてクラウドでの顔アルゴリズムの最も高度な Microsoft のサービスです。 *Face API* 2 つの主な機能: 属性を含む、検出して認識に直面します。 これにより、開発者、顔のグループのセットを設定するだけですし、次に、クエリ イメージ サービスへの送信後で、顔が属しているユーザーを決定します。 詳細については、次を参照してください。、 [Azure 顔認識ページ](https://azure.microsoft.com/services/cognitive-services/face/)します。

このコースを完了すると、複合現実は、次のことが、HoloLens のアプリケーションが用意されます。

1. 使用して、**タップ ジェスチャ**オンボード HoloLens カメラを使用してイメージのキャプチャを開始します。 
2. キャプチャしたイメージの送信、 *Azure の Face API*サービス。
3. 結果を受け取る、 *Face API*アルゴリズム。
4. 単純なユーザー インターフェイスを使用すると、一致したユーザーの名前を表示できます。

Face API のサービスから、Unity に基づく複合現実のアプリケーションに結果を取得する方法が説明されます。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 304:顔認識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。 (VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。 コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、記事.

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md)
- [最新の Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- (イマーシブ ヘッドセット開発) は、PC に接続されているカメラ
- Azure のセットアップおよび Face API 取得するためのインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1---the-azure-portal"></a>第 1 章 - Azure Portal

使用する、 *Face API*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  最初に、ログイン、 [Azure Portal](https://portal.azure.com)します。 

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して*Face API*、キーを押して**Enter**します。

    ![検索 api に直面](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

3.  新しいページがの説明を入力、 *Face API*サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![直面 api 情報](images/AzureLabs-Lab4-02.png)

4.  クリックすると**作成**:

    1. このサービス インスタンスのご希望の名前を挿入します。

    2. サブスクリプションを選択します。

    3. 作成時刻の場合、これは、最初に、適切な価格レベルを選択、 *Face API サービス*、(F0 という名前)、free レベルを使用することがあります。

    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. UWP アプリ、 **Person メーカー**、場所 '米国西部' の使用が必要です、後で使用します。

    6. また、このサービスに適用される条件を理解したことを確認する必要があります。

    7. 選択**作成 *。**

        ![作成直面 api サービス](images/AzureLabs-Lab4-03.png)

5.  クリックすると**作成 *** サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![サービスの作成の通知](images/AzureLabs-Lab4-04.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。

    ![リソース通知に移動します。](images/AzureLabs-Lab4-05.png)

8.  準備ができたら、クリックして**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。

    ![アクセス直面 api キー](images/AzureLabs-Lab4-06.png)

9.  内でのこのチュートリアルでは、アプリケーションは、サービスのサブスクリプション 'key' を使用して、これは、サービスへの呼び出しを実行する必要があります。 *クイック スタート* ページの*Face API*サービス、最初のポイントに番号は 1、*キーを取得します。*

10. *サービス*ページが青色のいずれかを選択します**キー**ハイパーリンク (クイック スタート ページの場合)、または**キー**サービスのナビゲーション メニューのリンク (によって示される、左側に、'キー ' アイコン)、キーを表示します。

    > [!NOTE] 
    > キーのいずれかの注意を受け取り、後で必要になると、保護します。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第 2 章 – 'Person メーカー' UWP アプリケーションの使用

呼ばれる事前構築済みの UWP アプリケーションをダウンロードすることを確認[Person メーカー](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)します。 このアプリは、このコースでは、単なるツール、以降のプロジェクトが依存している、Azure のエントリを作成するための最終的な製品ではありません。

**Person メーカー** 、人のユーザーとグループのユーザーに関連付けられている Azure のエントリを作成することができます。 アプリケーションは、後で使用できる、FaceAPI で追加した人物の顔を認識するための形式で、必要なすべての情報を配置します。 

> [重要]**Person メーカー**基本的な調整を使用して、サービス呼び出しの 1 分あたりの数を超えていないことを確保しやすく、**無料のサブスクリプション レベル**します。 上部にある緑のテキストは赤に変更され、調整が行われているときに、'ACTIVE' と更新大文字と小文字の場合は、(を待機する 'IN アクティブ' としてもう一度使用すると、更新、顔のサービスへのアクセスを次に続行できます)、アプリケーションの待機だけです。

このアプリケーションを使用して、 *Microsoft.ProjectOxford.Face*ライブラリは、完全にすることができる Face API を使用します。 このライブラリは NuGet パッケージとして無料で使用できます。 詳細についてと似ていますが、Api [API リファレンスの記事を参照してください。 確認](https://docs.microsoft.com/azure/cognitive-services/face/apireference)します。

> [!NOTE] 
> これらは、必要な手順だけ、これらの作業を行う方法については、ドキュメントの後半。 **Person メーカー**アプリでは、することはできます。
>
> - 作成、*人物グループ*を関連付ける複数のユーザーのグループが構成します。 Azure アカウントでは、複数のユーザー グループをホストできます。
>
> - 作成、 *Person*、人物グループのメンバーであります。 各ユーザーがさまざまな*Face*イメージが関連付けられています。
>
> -  割り当てる*イメージに直面*を*人*を認識する、Azure の Face API サービスのことを許可する、*人*、対応する*face*します。
>
> -  *トレーニング*、 *API サービスを Azure に直面*します。

ある人を認識するには、このアプリをトレーニングする場合、10 の拡大写真、ユーザー グループに追加したいが各ユーザーの必要があります。 ため注意してください。 Windows 10 の Cam アプリは、これらの考慮をするのに役立ちます。 それぞれの写真が明確であることを確認する必要があります (ぼかしやを隠ぺいすると、サブジェクトから離れすぎてを避ける)、jpg または png ファイル形式でないより大きいイメージ ファイルのサイズ、写真がある**4 MB**、いいえより小さい**1 KB**.

> [!NOTE]
> このチュートリアルに従っている場合は、上、HoloLens を保存する場合は、自分でを考察することはできません、トレーニングの独自の文字盤を使用しないでください。 仕事仲間や仲間の学生の顔を使用します。

実行している**Person メーカー**:

1.  開く、 **PersonMaker**フォルダー をクリックして、 *PersonMaker ソリューション*ファイルを開く*Visual Studio*します。

2.  1 回、 *PersonMaker ソリューション*を開いて、ことを確認します。

    1. *ソリューション構成*に設定されている**デバッグ**します。

    2. *ソリューション プラットフォーム*に設定されている**x86**

    3. *ターゲット プラットフォーム*は**ローカル マシン**します。

    4.  する必要があります*NuGet パッケージの復元*(を右クリックし、*ソリューション*選択**NuGet パッケージの復元**)。

3.  クリックして*ローカル マシン*され、アプリケーションが開始されます。 小さい画面に、注意してください、すべてのコンテンツは可能性がありますそれを表示するさらに下にスクロールできますが、表示されません。

    ![人の作成者のユーザー インターフェイス](images/AzureLabs-Lab4-07.png)

4.  挿入、 **Azure 認証キー**、する必要がありますが、これから、 *Face API*内での Azure サービスです。

5.  挿入します。

    1. *ID*に割り当てる、*人物グループ*します。 ID は、小文字、スペースなしである必要があります。 この id をメモしておいて後で、Unity プロジェクトで必要になります。
    2. *名前*に割り当てる、*人物グループ*(スペースを持つことができます)。


6.  キーを押して**人物グループの作成**ボタンをクリックします。 確認メッセージは、ボタンの下に表示されます。

> [!NOTE]
> ' アクセス拒否エラーが発生した場合は、Azure サービスに設定する場所を確認します。 前述のように、このアプリは米国西部"に設計されています。

> [!IMPORTANT]
> クリックすることできますも表示されます、**知られたグループをフェッチ**ボタン: 既にを作成したかどうか、人、新しく作成するのではなく、それを使用するには、グループ、および希望になります。 クリックする場合は注意*ユーザー グループを作成する*既知のグループと、グループをフェッチこれはもします。

7.  挿入、*名前*の*Person*を作成します。

    1. をクリックして、**ユーザーの作成**ボタンをクリックします。

    2. 確認メッセージは、ボタンの下に表示されます。

    3. 以前に作成した担当者を削除する場合は、キーを押してし、テキスト ボックスに名前を記述する**人物の削除**

8.  10 人のグループに追加したいユーザーの写真の場所を確認してください。

9.  キーを押して**の作成とフォルダーを開く**をユーザーに関連付けられているフォルダーに Windows エクスプ ローラーを開きます。 フォルダー内の 10 のイメージを追加します。 これらで必要があります*JPG*または*PNG*ファイル形式。

10. をクリックして**Azure に送信**します。 カウンターでは、メッセージを後に完了すると、送信の状態を表示します。

11. をクリック、カウンターが完了し、確認メッセージが表示されている**トレーニング**サービスをトレーニングします。

プロセスが完了すると、Unity に移動する準備が整いました。

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 - Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab4-08.png)

2.  これで、Unity プロジェクト名を指定する必要があります。 挿入**MR_FaceRecognition**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab4-09.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab4-10.png)

4.  次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab4-11.png)

5.  移動して**ファイル > Build Settings**ことを確認してください。

    1. **デバイスを対象に**に設定されている**HoloLens**

        > イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。

    2. **ビルドの種類**に設定されている**D3D**
    3. **SDK**に設定されている**インストールされている最新**
    4. **Visual Studio バージョン**に設定されている**インストールされている最新**
    5. **ビルドおよび実行**に設定されている**ローカル マシン**
    6. シーンを保存し、ビルドに追加します。 

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab4-12.png)

        2. 選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab4-13.png)

        3. 新たに作成した開く**シーン**フォルダー、し、**ファイル名**: テキスト フィールドに「 **FaceRecScene**、キーを押します**保存します**。

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab4-14.png)

    7. 設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

6. *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab4-15.png)

7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1. **Scripting** **ランタイム バージョン**べき**試験的**(.NET 4.6 Equivalent)。 これを変更すると、エディターを再起動する必要があるされます。
        2. **バックエンドの scripting**べき **.NET**
        3. **API の互換性レベル**べき **.NET 4.6**

            ![その他の設定を更新します。](images/AzureLabs-Lab4-16.png)
      
    2. 内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**
        - **Web カメラ**

            ![発行の設定を更新しています。](images/AzureLabs-Lab4-17.png)

    3. パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![X の R の設定を更新します。](images/AzureLabs-Lab4-18.png)

8.  戻り*Build Settings*、 **UnityC#プロジェクト**が不要になったグレー; これの横にあるチェック ボックスをオンにします。 
9.  ビルド設定ウィンドウを閉じます。
10. シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。

## <a name="chapter-4---main-camera-setup"></a>第 4 章 - メイン カメラのセットアップ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*のこのコンポーネントである、コース、コードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)、としてプロジェクトにインポート、[カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)します。 このパッケージにも、インポートが含まれることに注意してください、 *Newtonsoft DLL*の中で説明、[第 5 章](#chapter-5--import-the-newtonsoft.json-library)します。 このインポートから継続することができます[第 6 章](#chapter-6-create-the-faceanalysis-class)します。

1.  *階層*パネルで、選択、 **Main Camera**します。

2.  すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。

    1. **Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)。

    2. Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)。

    3. 必ず、**変換位置**に設定されている**0, 0, 0**

    4. 設定**フラグをクリア**に**純色**

    5. 設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (コードを 16 進数: #00000000)**

        ![カメラのコンポーネントを設定します。](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第 5 章 – Newtonsoft.Json ライブラリのインポート

> [!IMPORTANT]
> '.Unitypackage' をインポートした場合、[最後の章](#chapter-4--main-camera-setup)、この章をスキップすることができます。

逆シリアル化し、Bot Service の送受信にオブジェクトをシリアル化するのに役立つダウンロードする必要があります、 *Newtonsoft.Json*ライブラリ。 既にこの適切な Unity フォルダー構造を持つ構成されています。 互換性のあるバージョンを見つかります[Unity パッケージ ファイル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)します。 

ライブラリをインポートするには。

1.  Unity パッケージをダウンロードします。
2.  をクリックして**資産**、**パッケージ インポート**、**カスタム パッケージ**します。

    ![Newtonsoft.Json ライブラリをインポートします。](images/AzureLabs-Lab4-20.png)

3.  Unity パッケージをダウンロードして、し、[開く] をクリックします。
4.  確認、パッケージのすべてのコンポーネントがオン、を**インポート**します。

    ![Newtonsoft.Json ライブラリをインポートします。](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>第 6 章 - FaceAnalysis クラスを作成します。

FaceAnalysis クラスでは、Azure 顔の認識サービスとの通信に必要なメソッドをホストします。 

- キャプチャ イメージを送信すると、サービス、分析、および内で、顔の識別され既知のユーザーに属しているいずれかを判断します。 
- 既知のユーザーが見つかった場合、このクラスは、シーン内の UI テキストとして、名前を表示します。

作成する、 *FaceAnalysis*クラス。

 1. 右クリックし、 *Assets フォルダー*プロジェクト パネルにあるをクリックして**作成** > **フォルダー**します。 フォルダーを呼び出す**スクリプト**します。 

    ![FaceAnalysis クラスを作成します。](images/AzureLabs-Lab4-22.png)

2.  先ほど作成した、開くフォルダーをダブルクリックします。 
3.  フォルダー内を右クリックし、をクリックして**作成** >   **C#スクリプト**します。 スクリプトを呼び出す*FaceAnalysis*します。 
4.  新しいをダブルクリックします。 *FaceAnalysis*スクリプトを Visual Studio 2017 で開くことです。
5.  上記の次の名前空間を入力、 *FaceAnalysis*クラス。

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  すべての deserialising に使用されるオブジェクトを追加する必要があります。 これらのオブジェクトを追加する必要がある**外**の*FaceAnalysis* (下の中かっこ) の下のスクリプト。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start()* と*Update()* メソッドは使用されません、ようになりましたので削除します。 

8.  内で、 *FaceAnalysis*クラスで、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 置換、**キー**と**personGroupId**サービス キーと以前に作成したグループの Id。

9.  追加、 *Awake()* メソッドで、クラスを初期化するには、追加、 *ImageCapture* Main Camera クラス ラベルの作成メソッドを呼び出します。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 追加、 *CreateLabel()* メソッドで、作成、*ラベル*分析結果を表示するオブジェクト。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 追加、 *DetectFacesFromImage()* と*GetImageAsByteArray()* メソッド。 前者は後者は、キャプチャしたイメージをバイト配列に変換するために必要な送信済みのイメージのすべての可能な顔を検出するために、顔認識サービスを要求します。

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 追加、 *IdentifyFaces()* メソッドで、要求、*顔認識サービス*以前に送信されたイメージで検出された、既知の顔を識別するためにします。 要求には、特定の人が名ではなく id が返されます。

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 追加、 *GetPerson()* メソッド。 ユーザー id、このメソッドからの要求を提供することで、*顔認識サービス*識別されたユーザーの名前を返します。

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  **保存**Unity エディターに戻る前に変更します。
15.  Unity エディターで、[プロジェクト] パネルで、Scripts フォルダーから Main Camera オブジェクトに FaceAnalysis スクリプトをドラッグする、*階層パネル*します。 新しいスクリプト コンポーネントは、メイン カメラにので追加されます。 

![メイン カメラに FaceAnalysis を配置します。](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>7 - 章 ImageCapture クラスを作成します。

目的、 *ImageCapture*クラスとの通信に必要なメソッドをホストする、 *Azure 顔認識サービス*をそれに含まれる面を識別する、キャプチャするイメージを分析して既知のユーザーに属しているかどうかを決定します。 既知のユーザーが見つかった場合、このクラスは、シーン内の UI テキストとして、名前を表示します。

作成する、 *ImageCapture*クラス。
 
1.  内側を右クリックし、**スクリプト**フォルダーをクリックし、以前は、作成した**作成**、  **C#スクリプト**します。 スクリプトを呼び出す*ImageCapture*します。 
2.  新しいをダブルクリックします。 *ImageCapture*スクリプトを Visual Studio 2017 で開くことです。
3.  ImageCapture クラス上の次の名前空間を入力します。

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  内で、 *ImageCapture*クラスで、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  追加、 *Awake()* と*Start()* クラスを初期化し、ユーザーのジェスチャをキャプチャする HoloLens をできるようにするために必要なメソッド。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  追加、 *TapHandler()* 、ユーザーが実行するときに呼び出されるか、*タップ*ジェスチャ。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  追加、 *ExecuteImageCaptureAndAnalysis()* メソッドで、イメージのキャプチャのプロセスが開始されます。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  写真のキャプチャ プロセスが完了したときに呼び出されるハンドラーを追加します。

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. **保存**Unity エディターに戻る前に変更します。

## <a name="chapter-8---building-the-solution"></a>第 8 章 - ソリューションをビルドします。

アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。

実行する前にいることを確認します。

-   第 3 章で説明されているすべての設定が正しく設定されます。 
-   スクリプト*FaceAnalysis* Main Camera オブジェクトに接続されています。 
-   両方の**認証キー**と**グループ Id**内で設定されている、 *FaceAnalysis*スクリプト。

これをポイントするソリューションをビルドする準備が整いました。 ソリューションが作成されると、アプリケーションをデプロイする準備ができます。

ビルド プロセスを開始します。

1.  現在のシーンを保存するには、保存、ファイルをクリックします。
2.  開いているシーンを追加するファイル、ビルド設定 をクリックしてに移動します。
3.  Unity のティックにことを確認C#プロジェクト。

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-24.png)

4.  ビルドがキーを押します。 これを行う時に Unity が作成しにアプリをビルドするフォルダーを選択する必要がある、ファイル エクスプ ローラー ウィンドウを起動します。 Unity プロジェクト内で次に、そのフォルダーを作成し、アプリを呼び出します。 選択したアプリのフォルダー、フォルダーの選択キーを押します。 
5.  Unity では、アプリ フォルダーに、プロジェクトを構築が開始されます。 
6.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了した、ビルドの場所にファイル エクスプ ローラー ウィンドウが開きます。

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-25.png)

7.  [アプリ] フォルダーを開き、(上記のよう、MR_FaceRecognition.sln) 新しいプロジェクトのソリューションを開きます。


## <a name="chapter-9---deploying-your-application"></a>第 9 章 - アプリケーションのデプロイ

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

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab4-26.png)
 
5.  移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。
6.  アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。

> [!NOTE]
> イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。 ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。 


## <a name="chapter-10---using-the-application"></a>第 10 章 - アプリケーションの使用

1.  HoloLens、ソックスを着けずに、アプリを起動します。
2.  登録したユーザーを見て、 *Face API*します。 次のことを確認します。

    -  個人の顔がないと、遠と明確に表示
    -  環境光が暗すぎます。

3.  個人の写真をキャプチャするのにには、タップ ジェスチャを使用します。
4.  分析要求送信し、応答を受信するアプリを待ちます。
5.  ユーザーが正常に認識された場合、ユーザーの名前は、UI テキストとして表示されます。
6.  数秒ごと、タップ ジェスチャを使用して、キャプチャ プロセスを繰り返すことができます。

## <a name="your-finished-azure-face-api-application"></a>完成した Azure Face API アプリケーション

これで、イメージ内の顔を検出して、任意の既知の顔を識別する顔認識の Azure サービスを利用している mixed reality アプリを構築します。

![このコースを完了するの結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

**Azure の Face API** 1 つのイメージで最大 64 個の顔を検出するのに十分な強力です。 アプリケーションを拡張で他の多くの人々 の間で、2 つまたは 3 つの顔を認識する可能性があります。

### <a name="exercise-2"></a>手順 2

**Azure の Face API**がバックアップのすべての種類の属性情報を提供することもできます。 これをアプリケーションに統合します。 これは、さらに興味深いと組み合わせて、 [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)します。
