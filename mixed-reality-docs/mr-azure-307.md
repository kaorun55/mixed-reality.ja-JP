---
title: 307 - MR と Azure の Machine learning
description: このコースでは、複合現実のアプリケーション内で Azure Machine Learning Studio を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、machine learning、ml、machine learning studio、hololens、没入型、vr
ms.openlocfilehash: 726a6cce91d46ad878f8502381d085fb979ac72a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600281"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR と Azure 307 の場合:機械学習

![最終的な製品-開始](images/AzureLabs-Lab7-0.png)

このコースでは、Azure Machine Learning Studio を使用して複合現実のアプリケーションに機械学習 (ML) の機能を追加する方法を学びます。

*Azure Machine Learning Studio*は、開発者は多数の machine learning のアルゴリズムは、データ入力、出力、準備、およびビジュアル化に役立つ、Microsoft のサービスです。 これらのコンポーネントからの予測分析実験の開発、反復処理、およびモデルのトレーニングに使用することはします。 次のトレーニングを行うことができます、モデル運用 Azure のクラウド内で新しいデータをスコア付けできるようにします。 詳細については、次を参照してください。、 [Azure Machine Learning Studio ページ](https://azure.microsoft.com/en-au/services/machine-learning-studio/)します。

このコースを完了すると、複合現実イマーシブ ヘッドセット アプリケーションとは、次の操作方法を説明しました。

1.  テーブルを売上データの提供、 *Azure Machine Learning Studio*ポータル、および人気のある項目の将来の売上を予測するアルゴリズムを設計します。
2.  作成、 **Unity プロジェクト**、受信し、ML サービスからの予測データを解釈することができます。
3.  内の視覚的に predication データを表示、 **Unity プロジェクト**棚の上、最も人気のある販売品目を提供することにより、します。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

このコースは、他の複合現実ラボに直接関係は自己完結型のチュートリアルです。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 307 の場合:機械学習</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。 コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。 HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[インストール ツール記事](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、.

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- Azure のセットアップと ML データ取得のインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。 

## <a name="chapter-1---azure-storage-account-setup"></a>第 1 章 - Azure のストレージ アカウントのセットアップ

Azure Translator API を使用するには、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。
1.  ログイン、 [Azure Portal](https://portal.azure.com)します。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**ストレージ アカウント**左側のメニュー。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

3.  **ストレージ アカウント** タブで、をクリックして**追加**します。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-2.png)

4.  **ストレージ アカウントの作成**パネル。

    1.  挿入、**名前**お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。
    2.  **デプロイ モデルでは、** 選択**Resource manager**します。
    3.  **アカウントの種類**、**ストレージ (汎用 v1)** します。
    4.  **パフォーマンス**、**標準**します。
    5.  **レプリケーション**選択**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。
    6.  まま**転送が必須のセキュリティで保護された**として**無効になっている**します。
    7.  選択、**サブスクリプション**します。
    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。
    
    5.  確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。

5.  また、このサービスに適用される条件を理解したことを確認する必要があります。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-3.png)

6.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

7.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>第 2 章 – Azure の Machine Learning Studio

使用する、 *Azure Machine Learning*アプリケーションに使用可能にする Machine Learning サービスのインスタンスを構成する必要があります。

1.  Azure Portal をクリックして**新規**左上隅にある検索して**Machine Learning Studio ワークスペース**、キーを押して**Enter**。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  新しいページがの説明を入力、 **Machine Learning Studio ワークスペース**サービス。 このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、このサービスとの関連付けを作成します。

3.  クリックすると**作成**、新しいに関するいくつかの詳細を提供する必要があるパネルが表示されます**Machine Learning Studio service**:

    1.  必要な挿入**ワークスペース名**このサービス インスタンス。

    2.  選択、**サブスクリプション**します。

    3. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    4.  確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。 前の章で、Azure Storage を作成するために使用したのと同じリソース グループを使用する必要があります。

    5.  **ストレージ アカウント**セクションで、**既存**、ドロップダウン メニューで、をクリックしておよびそこから、をクリックして、**ストレージ アカウント**最後の章で作成しました。

    6.  適切な選択**ワークスペースの価格レベル**ドロップダウン メニューからできます。

    7.  内で、 **Web サービス プラン**セクションで、**作成** **、新しい**テキスト フィールドに名前を挿入します。

    8.  **Web サービス プランの価格レベル**セクションで、任意の価格レベルを選択します。 テストと呼ばれる層開発**DEVTEST 標準**料金なしで利用できるようにします。

    9.  また、このサービスに適用される条件を理解したことを確認する必要があります。

    10. **[作成]** をクリックします。

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

5.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  新しいサービス インスタンスを探索する通知をクリックします。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。

8.  表示されるページで、**その他のリンク**セクションで、 **Machine Learning Studio の起動**には、ブラウザーを直接は、 **Machine Learning Studio**ポータルです。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  使用して、**サインイン**ボタン、右上にあるか、センターで、Machine Learning Studio にログインします。

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>第 3 章 - Machine Learning Studio:データセットのセットアップ

機械学習アルゴリズムの動作方法の 1 つは既存のデータを分析し、将来の結果を予測しように基づいて既存のデータ セット。 通常、つまり、ほどアルゴリズムは将来の結果を予測するのにはするが、必要以上の既存のデータです。

サンプル テーブルは、このコースと呼ばれる[ProductsTableCSV ページでダウンロードできる](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)します。

> [!IMPORTANT]
> 上記の .zip ファイルには、両方が含まれています、 **ProductsTableCSV**と **.unitypackage**で必要になる[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)します。 このパッケージが csv ファイルに個別にも、その章で提供されます。

このサンプル データ セットには、2017 年の日付ごとの 1 時間ごとにベストセラーのオブジェクトのレコードが含まれています。
        
![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-11.png)

たとえば、2017年の 1 日目、午後 1 時 (時間 13) で、ベストセラー項目が塩とコショウします。

このサンプルのテーブルには、9998 エントリが含まれています。

1.  戻って、 **Machine Learning Studio**ポータル、としては、このテーブルを追加し、**データセット**ML の。 これをクリックすると、 **+ 新規**画面の左下隅のボタンをクリックします。

    ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-12.png)

2.  セクションを進めていくと内から下、左のナビゲーション パネルがあること。 クリックして**データセット**の右側に**ローカル ファイルから**します。

    ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-13.png)

3.  新しいアップロード**データセット**次の手順。

    1. 可能な場合、アップロードのウィンドウが表示**参照**新しいデータセットのハード ドライブ。

        ![Machine Learning Studio:データセットのセットアップ](images/AzureLabs-Lab7-14.png)

    2.  選択すると、し、[アップロード] ウィンドウに戻り、ティックのチェック ボックスをオンのままにします。

    3.  次のテキスト フィールドに入力**ProductsTableCSV.csv**データセットの名前として (ただし、自動的に追加する必要があります)。

    4.  ドロップダウン メニューを使用して**型**を選択します**汎用 CSV ファイル (.csv) ヘッダー**します。

    5.  アップロードのウィンドウの右下でチェック マークを押して、**データセット**がアップロードされます。

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>第 4 章 - Machine Learning Studio:実験

機械学習システムを作成するには、理論的には、データについての検証に、実験を作成する必要があります。 結果と共に、データと考えられる結果の間の相関関係がない場合または複数のデータが必要かどうかがわかります。

実験の作成を開始するには。

1.  再びクリックして、 **+ 新規**、ページの左下のボタンをクリックし、**実験** > **空白の実験**します。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-15.png)

2.  空白の実験では、新しいページが表示されます。

3.  左側の [展開] パネルから **保存されたデータセット*> *、* * データセットとドラッグ、 **ProductsTableCSV**に、**実験キャンバス**します。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-16.png)

4.  左側のパネルで **データ変換** > **サンプルおよび分割**します。 ドラッグし、 **データの分割** で項目を**実験キャンバス**します。 分割されたデータ項目では、データ セットを 2 つの部分に分割します。 機械学習アルゴリズムのトレーニングに使用する 1 つの部分。 2 番目の部分は生成されたアルゴリズムの精度を評価するためには。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-17.png)

5.  (キャンバス上の項目が選択されている分割データ) の中に右側のパネルで編集、**最初の出力データセット内の行の割合**に **0.7**します。 これは、データの 2 つの部分の分割、最初の部分は、データの 70% になります、および 2 番目の部分は、残りの 30% になります。 データがランダムに分割することを確認するため、確認、**ランダム分割**チェック ボックスが選択されます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-18.png)

6.  ベースからの接続をドラッグして、 **ProductsTableCSV**分割されたデータ項目の先頭に、キャンバス上の項目。 項目を接続が送信され、 **ProductsTableCSV**入力データを分割するデータセットの出力 (データ)。  

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-19.png)

7.  **実験**左側のパネルで、展開 **Machine Learning* > * トレーニング**します。ドラッグ、 **トレーニング モデル * * 内の項目を実験キャンバスにします。 キャンバスは同じになりますの下。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-20.png)

8.  ***左下にある***の**データの分割**項目への接続をドラッグして、**右を上位**の**モデルのトレーニング**項目。 アルゴリズムのトレーニングにモデルのトレーニングによってデータセットから最初の 70% の分割が使用されます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-21.png)

9.  選択、**モデルのトレーニング**項目と、キャンバスで、**プロパティ**(ブラウザーのウィンドウの右側にある) [パネル] をクリックして、 **列セレクターの起動** ボタンをクリックします。

10. テキスト ボックスに「**製品**しキーを押します**Enter**、*製品*予測をトレーニングする列として設定されます。 次に、をクリックして、**ティック**下部右上隅にある選択ダイアログ ボックスを閉じます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-22.png)

11. トレーニングする、**多クラス ロジスティック回帰**最も販売を予測するアルゴリズム**製品**曜日と日付の 1 時間に基づきます。 ただし、Azure Machine Learning studio で提供されるさまざまなアルゴリズムの詳細については、このドキュメントの範囲を超えては次のようにから詳細情報を調べることができます、 [Machine Learning アルゴリズム チート シート](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. 左側の実験項目パネルでは、次のように展開します * **Machine Learning* > *モデルの初期化*> * 分類 ***、ドラッグ、 **多クラス。ロジスティック回帰 * * を実験キャンバス上に項目。

13. 一番下から、出力を接続、**多クラス ロジスティック回帰**、左の入力に、**モデルのトレーニング**項目。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-23.png)

14. 左側のパネルの 実験項目の一覧で展開 **Machine Learning* > * スコア **、ドラッグ、 **スコア モデル * * をキャンバス上に項目。

15. 一番下から、出力を接続、 **モデルのトレーニング**、左の入力に、 **モデルのスコア付け**します。

16. 右下の出力を接続 **データの分割**、右の入力に、**モデルのスコア付け* 項目 *。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-24.png)

17. 一覧で**実験**、左側のパネルでアイテムの展開 * **Machine Learning* > * 評価 ***、ドラッグ、 **をキャンバスに項目を評価モデル * *。

18. 出力を接続、 **モデルのスコア付け** の左の入力に、 **モデルの評価**します。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-25.png)

19. 最初の Machine Learning の実験を構築したとします。 保存し、実験を実行できます。 ページの下部にあるメニューをクリックして、**保存**ボタンをクリックして、実験を保存**実行**実験の先頭にします。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-26.png)

20. 確認できます、**状態**実験キャンバスの上部右にあるのです。 実験を完了するまで数分を待機します。

    > ビッグ (実際) のデータセットがある場合は、実験に実行する時間がかかる場合があります、高くなります。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-27.png)

21. 右クリックして、**モデルの評価**キャンバスでは、コンテキスト メニュー ホバーからマウスで項目 **評価の結果を**を選択し、**視覚化**します。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-28.png)

22. 実際の結果と予測結果を表示、評価結果が表示されます。 これは、モデルの評価が以前では、分割された元のデータセットの 30% を使用します。 結果は優れた、理想的には必要があります最上位の番号各行の列に含められる、選択された項目を確認できます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-29.png)

23. 閉じる、**結果**します。

24. として公開する必要がある、新しくトレーニングされた機械学習モデルを使用する、 **Web サービス**します。 これを行うには、をクリックして、 **Web サービスの設定** メニューで、ページの下部にあるメニュー項目をクリックします **予測 Web サービス**します。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-30.png)

25. 新しいタブが作成され、モデルのトレーニングは、新しい web サービスを作成するマージします。 

26. ページの下部にあるメニューでクリックして**保存**、順にクリックします**実行**します。 実験キャンバスの右上隅にある更新の状態が表示されます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-31.png)

27. 実行が完了すると、 **Web サービスのデプロイ**ボタンがページの下部に表示されます。 Web サービスをデプロイする準備が整いました。 クリックして **Web サービスのデプロイ**ページの下部にあるメニューでは (クラシック)。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-32.png)

    > お使いのブラウザーが行う必要がありますポップアップを許可する要求があります**許可**キーを押す必要がありますが、 **Web サービスのデプロイ**、もう一度デプロイ ページが表示されない場合。 

28. 実験を作成した後にリダイレクトされます、**ダッシュ ボード**する必要があるページ、 **API キー**が表示されます。 今のところ、メモ帳にコピー、必要になるコードに非常に早くします。 をクリックすると、API キーをメモ、**要求/応答**ボタン、**既定のエンドポイント**セクション、キーの下にあります。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > このページで [テスト] をクリックした場合は、入力データを入力し、出力を表示することができます。 入力、**日**と**時間**します。 ままに、**製品**空白エントリ。 をクリックし、 **確認**ボタンをクリックします。 選択されている各製品の尤度を表す JSON は、ページの下部にある出力が表示されます。

29. 新しい web ページが指示と、Machine Learning Studio で必要な要求の構造について例をいくつかの表示を開きます。 コピー、**要求 URI**メモ帳に、このページに表示されます。

    ![Machine Learning Studio:実験](images/AzureLabs-Lab7-34.png)

Machine learning の日、年の通算日の時間に関連付け、購入履歴データに基づいて、販売できる可能性が最も高い製品を提供するシステムをビルドが完了しました。

Web サービスを呼び出すには、サービス エンドポイントとサービスの API キーの URL を必要があります。 をクリックして、 **Consume**  タブで、上部のメニューから。

**消費**情報 ページをコードから web サービスを呼び出す必要があります情報が表示されます。 コピーを作成、**主キー**と**要求-応答**URL。 [次へ] の章で必要になります。

## <a name="chapter-5---setting-up-the-unity-project"></a>第 5 章 - Unity プロジェクトの設定

設定し、混合 Reality イマーシブ ヘッドセットをテストします。

> [!NOTE]
>  **いない**このコースのモーションのコント ローラーが必要です。 イマーシブ ヘッドセットの設定をサポートする場合をクリックしてください[ここ](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。

1.  開いている**Unity**という新しい Unity プロジェクトを作成および**MR\_MachineLearning します。** 必ず、プロジェクトの種類に設定されて**3D**します。

2.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して***編集* > *設定*** し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

3.  次に移動***ファイル* > *Build Settings*** にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして***スイッチ プラットフォーム***ボタンをクリックします。

4.  確認します。

    1.  **デバイスを対象に**に設定されている**任意のデバイス**します。

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2.  **ビルドの種類**に設定されている**D3D**します。

    3.  **SDK**に設定されている**インストールされている最新**します。

    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**します。

    5.  **ビルドおよび実行**に設定されている**ローカル マシン**します。

    6.  設定する方法について気にかけないように**シーン**、現時点で、これらは後で説明します。

    7.  残りの設定は、ここでは、既定値として残しておく必要があります。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-35.png)

5.  **Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。 

6. このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **Scripting** **ランタイム バージョン**べき**試験的**(.NET 4.6 Equivalent)

        2. **バックエンドの scripting**べき ***.NET***

        3. **API の互換性レベル**べき **.NET 4.6**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-36.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-37.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-38.png)

    

6.  戻り**Build Settings** *Unity C#* プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。 

7.  ビルド設定ウィンドウを閉じます。

8.  プロジェクトを保存 (**ファイル > プロジェクトを保存**)。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第 6 章 – MLProducts Unity パッケージをインポートします。

このコースでは、という名前の Unity アセット パッケージをダウンロードする必要があります[ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)します。 このパッケージは、すべてのオブジェクトを使用した、シーンを構築済みので、すべての作業に集中できます。 **ShelfKeeper**スクリプトを提供すると、ただしのみシーン セットアップ構造の目的で、パブリック変数が保持されます。 その他のすべてのセクションを実行する必要があります。 

このパッケージをインポートするには。

1.  前 Unity ダッシュ ボード をクリックして**資産**画面の上部にあるメニューでクリックして**Import Package、カスタム パッケージ**します。

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-39.png)

2.  ファイル ピッカーを使用して、 **Azure-MR-307.unitypackage**パッケージ化し、をクリックして**オープン**します。

3.  この資産のコンポーネントの一覧が表示されます。 クリックして、インポートを確認します。**インポート**します。

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-40.png)

4.  インポートが完了、いくつかの新しいフォルダーが、Unity で登場したことがわかりますが**プロジェクト パネル**します。 これらは、3 D モデルとそれぞれの資料では、事前に作成されたシーンの部分です。 このコースでは、コードの大部分を記述します。

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-41.png)

5.  内で、**プロジェクト パネル**フォルダーをクリックして、**シーン**フォルダー、double、シーン内をクリックする (と呼ばれる**MR_MachineLearningScene**)。 シーンが開きます (下図を参照してください)。 赤い菱形が不足している場合は、クリックして、**ギズモ**上部のボタンの右、**ゲーム パネル**。

    ![MLProducts Unity パッケージをインポートします。](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第 7 章 - Unity で Dll を確認

(シリアル化と逆シリアル化に使用)、JSON ライブラリの使用を活用して、Newtonsoft DLL で取り込まれたパッケージに実装されています。 ライブラリは、(特に問題が発生したコードが動作していない) 場合を確認する必要が、構成を適切にすることが必要です。 

次の手順に従います。

-  Plugins フォルダー内のファイルを Newtonsoft を左クリックを見て、**インスペクター パネル**します。 確認**Any プラットフォーム**がオンになっています。 移動、 **UWP タブ**も確認してください**処理しない**がオンになっています。

    ![Unity で、Dll のインポート](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>8 - 章 ShelfKeeper クラスを作成します。

**ShelfKeeper**クラスは、UI とシーンで製品を制御するメソッドをホストします。

インポート元のパッケージの一部としてが与えられているこのクラスは、不完全な場合。 そのクラスの所要時間はようになりました。

1.  ダブルクリック、 **ShelfKeeper**スクリプト内で、**スクリプト**フォルダー、ファイルを開く**Visual Studio 2017**します。

2.  既存の日付と時刻を設定し、製品を表示するメソッドを持つ次のコードでのスクリプトですべてのコードに置き換えます。

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

4.  Unity エディターで戻ることを確認、 **ShelfKeeper**クラスの下。

    ![ShelfKeeper クラスを作成します。](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > スクリプト参照のターゲットを持たない場合 (つまり *(テキスト メッシュ) 日付*) から対応するオブジェクトをドラッグするだけ、**階層パネル**、ターゲット フィールドにします。 以下をご覧ください詳細については、必要な場合。
    > 
    > 1.  開く、 **Spawn ポイント**内で配列、 **ShelfKeeper**をクリックしてコンポーネントのスクリプト。 サブ セクションが呼び出された表示**サイズ**配列のサイズを示します。 型**3**  の隣にテキスト ボックスに**サイズ**キーを押します**Enter**、下にある 3 つのスロットが作成されます。
    > 2. 内で、**階層**展開、**時間表示**(横にある矢印をクリック) でのオブジェクト。 次にをクリックして、 ***Main Camera***内から、**階層**するように、**インスペクター**その情報が表示されます。
    > 3. 選択、**メイン カメラ**で、**階層パネル**します。 ドラッグ、**日付**と**時間**オブジェクトから、**階層パネル**を**日付のテキスト**と**時テキスト**内のスロット、**インスペクター**の**Main Camera**で、 **ShelfKeeper**コンポーネント。
    > 4. ドラッグ、 **Spawn ポイント**から、**階層パネル**(下にある、*棚*オブジェクト) を**3** **要素**下にあるターゲットの参照、 **Spawn ポイント**配列を図のようにします。
    > 
    >     ![ShelfKeeper クラスを作成します。](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>9 - 章 ProductPrediction クラスを作成します。

次のクラスを作成することには、 **ProductPrediction**クラス。

このクラスは、責任を負います。

-   クエリを実行する、 **Machine Learning サービス**インスタンス、現在の日付と時刻を提供します。

-   使用可能なデータには、JSON 応答を逆シリアル化します。

-   推奨される 3 つの製品を取得する、データを解釈します。

-   呼び出す、 **ShelfKeeper**クラス、シーン内のデータを表示するメソッド。

このクラスを作成します。

1.  移動して、**スクリプト**フォルダーで、**プロジェクト パネル**します。

2.  フォルダー内を右クリックして**作成** > **C\#スクリプト**します。 スクリプトを呼び出す**ProductPrediction**します。

3.  新しいをダブルクリックします。 **ProductPrediction**スクリプト ファイルを開く**Visual Studio 2017**します。

4.  場合、**ファイル変更の検出**ダイアログ ポップアップ、 をクリック ***ソリューションの再読み込み**します。

5.  ProductPrediction クラスの先頭に次の名前空間を追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  内で、 **ProductPrediction**クラスは、多数の入れ子になったクラスの構成は次の 2 つのオブジェクトを挿入します。 これらのクラスは、Machine Learning サービスの JSON を逆シリアル化およびシリアル化に使用されます。

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  (その JSON では、コードは、以下の他のすべてのコードとの間の方法は、スクリプトの下部に関連する) は、前のコードの上、次の変数を追加します。

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > 挿入することを確認、**主キー**と**要求-応答エンドポイント**、マシン ラーニング ポータルでの変数をここにします。 イメージの下には、場所が取得したキーとエンドポイントを表示します。 
    >  
    > ![Machine Learning Studio:実験](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio:実験](images/AzureLabs-Lab7-53-2.png)

8.  このコード内で挿入、 **Start()** メソッド。 **Start()** クラス初期化メソッドが呼び出されます。

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Windows から日付と時刻を収集し、Machine Learning の実験は、テーブルに格納されたデータを比較に使用できる形式に変換するメソッドを次に示します。

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. できます**削除**、 **Update()** メソッドのため、このクラスは使用されません。

11. 現在の日付と時刻を Machine Learning のエンドポイントと通信、JSON 形式で応答を受信する次のメソッドを追加します。

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. JSON の応答を逆シリアル化およびを逆シリアル化の結果との通信を担当する次のメソッドを追加、 **ShelfKeeper**クラス。 この結果は、現在の日付と時刻にほとんどの販売を予測する 3 つの項目の名前になります。 次のコードを挿入、 **ProductPrediction**前のメソッドの下のクラス。

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. 保存**Visual Studio**に戻る**Unity**します。

14. ドラッグ、 **ProductPrediction**クラスからのスクリプト、**スクリプト**フォルダーに、 **Main Camera**オブジェクト。

15. シーンとプロジェクトを保存**ファイル** > ***Save Scene* / *ファイル***  >  **プロジェクトを保存**します。

## <a name="chapter-10---build-the-uwp-solution"></a>第 10 章 – UWP ソリューションのビルド

今度は UWP ソリューションでプロジェクトをビルドするには、スタンドアロン アプリケーションとして実行できるようにします。

作成する方法。

1.  現在のシーンを保存 をクリックして**ファイル****保存シーン**します。

2.  移動して**ファイル****ビルド設定**

3.  チェック ボックスと呼ばれる**Unity C\#プロジェクト**(これは重要なビルドが完了した後に、クラスを編集することを許可することがあるため)。

4.  をクリックして**開くシーンを追加**、

5.  **[Build]** をクリックします。

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-54.png)

6.  ソリューションをビルドするフォルダーを選択するように促されます。

7.  作成、**ビルド**フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。

8.  新しいフォルダーをクリックし、クリックして**フォルダーの選択**の場所にビルドを開始します。

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-55.png)

    ![UWP のソリューションを構築します。](images/AzureLabs-Lab7-56.png)

9.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-11---deploy-your-application"></a>章 11 - アプリケーションをデプロイします。

アプリケーションを配置します。

1.  新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。

2.  Visual Studio を開き、NuGet パッケージの復元、MachineLearningLab_Build ソリューション、ソリューション エクスプ ローラーを (Visual Studio の右側にあります) を右クリックし、NuGet パッケージの復元を行うことが可能にする必要があります。

    ![NuGet パッケージを追加します。](images/AzureLabs-Lab7-57.png)

3.  ソリューション構成の選択で**デバッグ**します。

4.  ソリューション プラットフォーム で選択**x86**、**ローカル マシン**します。 

    > Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。 ただし、次の操作も必要があります。
    > - 把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。 
    > - 確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。

    ![NuGet パッケージを追加します。](images/AzureLabs-Lab7-58.png)

5.  移動して**ビルド メニュー**  をクリック**ソリューションの配置**を PC にアプリケーションをサイドローディングします。

6.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。

複合現実のアプリケーションを実行するときに Unity シーンに設定されていたベンチは表示され、初期化、Azure 内で設定したデータのフェッチされます。 データは、アプリケーション内に逆シリアル化して、現在の日付と時刻の上位 3 つの結果を視覚的に、3 つのモデル、ベンチで提供されます。


## <a name="your-finished-machine-learning-application"></a>完成した Machine Learning アプリケーション
 
これで、データの予測を作成し、シーンに表示する Azure Machine Learning を利用している mixed reality アプリを構築します。

![NuGet パッケージを追加します。](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>演習

**手順 1**

実験で、アプリケーションの並べ替え順序あり、このデータ可能性のある役に立つことも、棚に表示される下部にある 3 つの予測が。

**手順 2**

使用して**Azure Tables**気象情報を含む新しいテーブルを設定して、データを使用して新しい実験を作成します。
