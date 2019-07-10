---
title: MR、および Azure 308 - クロス デバイスの通知
description: このコースでは、複合現実のアプリケーション内で Azure Notification Hubs、Azure Functions と Azure Storage、およびテーブルを実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、通知、関数、テーブル、hololens、没入型、vr、notification hubs
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694603"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR と Azure 308:クロス デバイスの通知

![最終的な製品-開始](images/AzureLabs-Lab8-00.png)

このコースでは、Azure Notification Hubs、Azure テーブル、および Azure Functions を使用して、複合現実のアプリケーションに Notification Hubs の機能を追加する方法を学びます。

**Azure Notification Hubs**はにより、開発者は、クラウド内ですべて電源任意のプラットフォームを対象となる、パーソナライズされたプッシュ通知を送信する、Microsoft のサービスです。 開発者は、エンドユーザーとの通信を効果的に許可したり、シナリオに応じて、さまざまなアプリケーション間の通信もできます。 詳細については、次を参照してください。、 **Azure Notification Hubs** [ページ](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)します。

**Azure Functions**できる小規模なコードを実行する開発者の Microsoft サービス '関数'、Azure では、します。 これは、多くのメリットを持つことができる、ローカル アプリケーションではなく、クラウドに作業を委任する方法を提供します。 **Azure Functions** C をなど、複数の開発言語をサポートしている\#、F\#Node.js、Java、および PHP します。 詳細については、次を参照してください。、 **Azure Functions** [ページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)します。

**Azure テーブル**開発者が、クラウドで構造化された非 SQL データを格納する、Microsoft クラウド サービスを得ることが簡単にアクセスできる任意の場所。 サービスは、スキーマレス設計になっているため、必要に応じて、テーブルの進化は幅広いプラットフォーム、非常に柔軟なは。 詳細については、次を参照してください、 **Azure Tables** [ページ。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

このコースを完了すると、複合現実、イマーシブ ヘッドセット アプリケーションと、以下を実行できる必要がデスクトップ PC のアプリケーションが用意されます。

1. デスクトップ PC のアプリが (X および Y) の 2 次元空間でオブジェクトを移動するユーザーを許可する、マウスを使用します。

2. PC のアプリ内のオブジェクトの移動では、文字列の形式になります JSON を使用して、型、オブジェクト ID を格納しているクラウドに送信され、(X と Y 座標) の情報を変換します。 

3. デスクトップ アプリに同一のシーンのある、mixed reality アプリでは、(これは、デスクトップ PC のアプリで更新されただけですが)、Notification Hubs サービスからオブジェクトの移動に関する通知を受け取ります。 

4. オブジェクト ID、型、および変換の情報には、通知を受信すると、mixed reality アプリで受信した情報を独自のシーンに適用されます。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。 このコースは、他の複合現実ラボに直接関係は自己完結型のチュートリアルです。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 308:クロス デバイスの通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Azure のセットアップと Notification Hubs へのアクセスにインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

- このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
- Microsoft 開発者ポータルと、アプリケーション登録ポータルの所有者である必要がある、それ以外の場合でアプリにアクセスする権限があるがない[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)します。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Chapter 1 - Microsoft 開発者ポータルでアプリケーションを作成します。

使用する、 **Azure Notification Hubs**サービス、する必要があります、Microsoft 開発者ポータルでアプリケーションを作成するように、アプリケーションが送信して通知を受信できるように登録する必要があります。

1.  ログイン、 [Microsoft 開発者ポータル](https://developer.microsoft.com/dashboard)します。

    > Microsoft アカウントにログインする必要があります。

2.  ダッシュ ボードで、次のようにクリックします。**新しいアプリを作成**です。

    ![アプリを作成します。](images/AzureLabs-Lab8-01.png)

3.  新しいアプリの名前を予約する必要があります、ポップアップが表示されます。 ボックスに、適切な名前では; を挿入します。選択した名前を使用できる場合、テキスト ボックスの右側にチェック マークが表示されます。 挿入された、使用可能な名前を作成したら、 をクリックして、**製品名の予約**ポップアップの左下にボタンをクリックします。

    ![名前を反転します。](images/AzureLabs-Lab8-02.png)

4.  ここで作成したアプリケーション、[次へ] の章に移動する準備が完了したら。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Chapter 2 - 新しいアプリ資格情報を取得します。

新しいアプリが表示され、セットアップに使用される資格情報を取得、アプリケーション登録ポータルにログイン、 **Notification Hubs サービス**内、 **Azure Portal**します。

1.  移動し、[アプリケーション登録ポータル](http://apps.dev.microsoft.com)します。

    ![アプリケーション登録ポータル](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > ログインに Microsoft アカウントを使用する必要があります。  
    > これは、**する必要があります**、以前使用した Microsoft アカウントである[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)、Windows ストア開発者ポータルを使用しました。

2.  下でアプリが表示されます、**アプリケーション**セクション。 クリックして、アプリを新しいページに表示されますが見つかった場合、名前と**登録**します。

    ![新しく登録されたアプリ](images/AzureLabs-Lab8-04.png)

3.  スクロール登録ページを参照して、**アプリケーション シークレット**セクションおよび**パッケージ SID**アプリ。 セットアップで使用するための両方をコピー、 **Azure Notification Hubs サービス**[次へ] の章。

    ![アプリケーション シークレット](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>3 - Azure ポータルのセットアップの章: Notification Hubs サービスの作成します。

Apps の資格情報を取得するには、Azure Notification Hubs サービスを作成する、Azure Portal に移動する必要があります。

1.  [Azure ポータル](https://portal.azure.com) にログインします。

    > [!NOTE] 
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して**Notification Hub**、 をクリック***Enter***。

    ![通知ハブの検索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 単語***新規***に置き換えられました**リソースの作成**、新しいポータルでします。

3.  新しいページがの説明を入力、 *Notification Hubs*サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![notification hubs のインスタンスを作成します。](images/AzureLabs-Lab8-07.png)

4.  クリックすると***作成***:

    1.  このサービス インスタンスのご希望の名前を挿入します。

    2.  提供、**名前空間**がこのアプリに関連付けることができます。

    3.  選択、**場所。**

    4.  選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。 

    5.  適切な選択**サブスクリプション**します。

    6.  また、このサービスに適用される条件を理解したことを確認する必要があります。

    7. **[作成]** を選択します。

        ![サービスの詳細を入力します。](images/AzureLabs-Lab8-08.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![通知 (notification)](images/AzureLabs-Lab8-09.png)

7.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 実施する、新しい**Notification Hub**サービス インスタンス。

    ![リソースに移動します。](images/AzureLabs-Lab8-10.png)
    
8.  概要 ページで、ページの真ん中からクリックして**Windows (WNS)。** 右側のパネルを必要とする 2 つの表示テキスト フィールドに変更は、**パッケージ SID**と**セキュリティ キー**、以前設定したアプリから。

    ![新しく作成したハブのサービス](images/AzureLabs-Lab8-11.png)

9. 詳細は、適切なフィールドにコピーした、したら**保存**、通知ハブが正常に更新されたときに通知が表示されます。

    ![セキュリティの詳細をコピーします。](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>4 - Azure ポータルのセットアップの章: Table Service の作成します。

Notification Hubs のサービス インスタンスを作成した後は、ストレージ リソースを作成して、Azure テーブル サービスを作成する、Azure ポータルに戻る移動します。

1.  サインインしていない場合のログイン、 [Azure Portal](https://portal.azure.com)します。

2.  ログインすると、をクリックして**新規**左上隅にある検索して**ストレージ アカウント**、 をクリック**Enter**します。

    > [!NOTE] 
    > 単語***新規***に置き換えられました**リソースの作成**、新しいポータルでします。

3.  選択**ストレージ アカウント - blob、ファイル、テーブル、キュー**一覧から。

    ![ストレージ アカウントの検索](images/AzureLabs-Lab8-13.png)

4.  新しいページがの説明を入力、**ストレージ アカウント**サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスのインスタンスを作成します。

    ![ストレージのインスタンスを作成します。](images/AzureLabs-Lab8-14.png)

5.  クリックすると**作成**パネルが表示されます。

    1. 必要な挿入**名前**(すべて小文字にする必要があります)、このサービス インスタンス。

    2. **デプロイ モデル**、 をクリックして**Resource manager**します。

    3.  **アカウントの種類**、ドロップダウン メニューを使用して、選択**ストレージ (汎用 v1)** します。

    4. 適切な選択**場所**します。
    
    5.  **レプリケーション**ドロップダウン メニューで、**読み取りアクセスの geo 冗長ストレージ (RA-GRS)** します。

    6.  **パフォーマンス**、 をクリックして**標準**します。

    7.  内で、**転送が必須のセキュリティで保護された**セクションで、**無効**します。

    8.  **サブスクリプション**ドロップダウン メニューで、適切なサブスクリプションを選択します。

    9.  選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    10. まま**仮想ネットワーク**として**無効になっている**するためのオプションの場合。

    11. **[作成]** をクリックします。

        ![ストレージの詳細を入力します。](images/AzureLabs-Lab8-15.png)

6.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

7.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。 新しいサービス インスタンスを探索する通知をクリックします。

    ![新しい記憶域の通知](images/AzureLabs-Lab8-16.png)

8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 新しい記憶域のサービス インスタンスの概要ページが表示されます。

    ![リソースに移動します。](images/AzureLabs-Lab8-17.PNG)

9. 概要 ページの右側にあるをクリックします。**テーブル**します。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 右側のパネルを表示する変更は、 **Table service**については、の新しいテーブルを追加する必要があります。 クリックして、 **+** **テーブル**ボタンの左上隅をクリックします。

    ![テーブルを開く](images/AzureLabs-Lab8-19.png)

11. 入力する必要があります、新しいページが表示されます、**テーブル名**します。 これは、以降の章で、アプリケーションでデータを指すために使用する名前です。 適切な名前を挿入し、をクリックして**OK**します。

    ![新しいテーブルを作成します。](images/AzureLabs-Lab8-20.png)    

12. 新しいテーブルが作成されたら、できなく内を確認する、 **Table service** (下部) のページ。

    ![新しいテーブルの作成](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第 5 章 - Visual Studio で Azure テーブルの完了

これで、 **Table service**ストレージ アカウントを設定したら、情報格納および取得するために使用するデータを追加する時間。 テーブルの編集を実行できます**Visual Studio**します。

1.  開いている**Visual Studio**します。

2.  メニューから、次のようにクリックします。**ビュー** > **Cloud Explorer**します。

    ![クラウド エクスプ ローラーを開く](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer** (に患者、読み込み時間がかかる場合があります) がドッキングされている項目として開きます。

    > [!NOTE] 
    > サブスクリプションの作成に使用する場合、*ストレージ アカウント*が表示されないできることを確認します。 
    > - Azure Portal を使用したものと同じアカウントにログインします。
    > - (アカウント設定からフィルターを適用する必要があります)、アカウント管理ページからサブスクリプションを選択します。  
    >
    >   ![サブスクリプションが見つかりません](images/AzureLabs-Lab8-22-5.png)

4.  Azure クラウド サービスが表示されます。 検索**ストレージ アカウント**アカウントを展開するの左側にある矢印をクリックします。

    ![ストレージ アカウント を開きます](images/AzureLabs-Lab8-23.png)

5.  展開されている場合、新しく作成した後**ストレージ アカウント**できるようにします。 ストレージの左側にある矢印をクリックしを展開したら探します**テーブル**を表示する横の矢印をクリックします、**テーブル**最後の章で作成しました。 ダブルクリックして、**テーブル**します。

    ![シーン オブジェクト テーブルを開く](images/AzureLabs-Lab8-24.png)

6.  テーブルには、Visual Studio ウィンドウの中央に開かれます。 テーブル アイコンをクリックして、 **+** には、(+)。

    ![新しいテーブルを追加します。](images/AzureLabs-Lab8-25.png)

7.  ウィンドウがするためのプロンプトを表示する表示*エンティティの追加*します。 いくつかのプロパティを持つ、合計で 3 つのエンティティを作成します。 わかります*PartitionKey*と*RowKey*が既に提供されている、使用される場合は、テーブルでデータを検索します。 

    ![パーティションと行キー](images/AzureLabs-Lab8-26.png)

8. 更新プログラム、*値*の**PartitionKey**と**RowKey**次のように (各行プロパティを追加すると、これを行っても、RowKey を毎回インクリメント)。

    ![正しい値を追加します。](images/AzureLabs-Lab8-26-5.png)

9.  クリックして**プロパティを追加**余分なデータ行を追加します。 空テーブルの最初に一致する、次の表。

10. クリックして**OK**は終了するとき。

    ![実行時に、[ok] をクリックします。](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 変更したことを確認、**型**の**X**、 **Y**、および**Z**、エントリを**二重**します。 

11. テーブル内のデータ行のようになりましたが表示されます。 をクリックして、 **+** (+) アイコンをもう一度別のエンティティを追加します。

    ![最初の行](images/AzureLabs-Lab8-27-5.png)

12. 追加のプロパティを作成し、次に示すものと一致する新しいエンティティの値を設定します。

    ![キューブを追加します。](images/AzureLabs-Lab8-28.png)

13. 別のエンティティを追加する最後の手順を繰り返します。 次のように、このエンティティの値を設定します。

    ![円柱を追加します。](images/AzureLabs-Lab8-29.png)

14. テーブルには、次のようになります。

    ![完全なテーブル](images/AzureLabs-Lab8-30.png)

15. この章は完了しました。 保存してください。

## <a name="chapter-6---create-an-azure-function-app"></a>第 6 章 - Azure Function App を作成します。

更新するデスクトップ アプリケーションによって呼び出される、Azure Function App を作成、**テーブル**サービスし、の通知を送信、 **Notification Hub**します。

最初に、必要なライブラリの読み込みに、Azure 関数を許可するファイルを作成する必要があります。

1.  開いている**メモ帳**(Windows キーと型のメモ帳にキーを押します)。

    ![メモ帳を開く](images/AzureLabs-Lab8-31.png)

2.  メモ帳を開く、そこに以下の JSON 構造を挿入します。 完了したら、としてデスクトップに保存**project.json**します。 名前の付け方が正しいことが重要になります: はことを確認 **、.txt が付いていない**ファイル拡張子。 分かります NuGet を使用している場合、このファイルは、関数を使用するには、ライブラリを定義します。

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  [Azure ポータル](https://portal.azure.com) にログインします。

4.  ログインした後は、をクリックして**新規**左上隅にある検索して**Function App**、キーを押して**Enter**。

    ![関数アプリの検索](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。

5.  新しいページがの説明を入力、 **Function App**サービス。 このプロンプトの左下にある at、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![関数アプリ インスタンス](images/AzureLabs-Lab8-33.png)

6.  クリックすると**作成**次を入力します。

    1. **アプリ名**、このサービス インスタンスのご希望の名前を挿入します。

    2. 選択、**サブスクリプション**します。

    3. 作成時刻の場合、これは、最初に、適切な価格レベルを選択、 **Function App サービス**、free レベルを使用することがあります。

    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。

        > 詳細にする場合について、Azure リソース グループに従ってくださいこの[リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. **OS**、目的のプラットフォームであるために、Windows をクリックします。

    6. 選択、**ホスティング プラン**(このチュートリアルを使用して、**従量課金プラン**します。

    7. 選択、**場所** **(前の手順で作成したストレージと同じ場所を選択)**

    8. **ストレージ**セクション **、前の手順で作成したストレージ サービスを選択する必要があります**します。

    9. 必要はありません*Application Insights*このアプリでため、自由に**オフ**します。

    10. **[作成]** をクリックします。

        ![新しいインスタンスを作成します。](images/AzureLabs-Lab8-34.png)

7.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

8.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![新しい通知](images/AzureLabs-Lab8-35.png)

9.  新しいサービス インスタンスを探索する通知をクリックします。

10. をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 

    ![リソースに移動します。](images/AzureLabs-Lab8-36.png)

11. をクリックして、 **+** (隣にアイコン +)*関数*を*新規作成*です。

    ![新しい関数を追加します。](images/AzureLabs-Lab8-37.png)

12. 中央のパネル内、**関数**作成ウィンドウが表示されます。 パネルの上半分に情報を無視し、をクリックして**カスタム関数**、(次に示すよう青い領域) の下の方に配置されています。

    ![カスタム関数](images/AzureLabs-Lab8-38.png)

13. ウィンドウ内で新しいページには、さまざまな関数の型が表示されます。 紫の種類を表示するスクロールし、をクリックして**HTTP PUT**要素。

    ![http のリンクを配置します。](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > さらに、リストをスクロールする必要があります、ページ (と、このイメージが正確に同じですが、Azure ポータルの更新が行われた場合) と呼ばれる要素を検索するただし、 *HTTP PUT*します。

14. **HTTP PUT**ウィンドウが表示されます (以下参照イメージの) 機能を構成する必要があります。

    1.  **言語**C を選択して、ドロップダウン メニューを使用して\#します。

    2.  **名、** 適切な名前を入力します。

    3.  **認証レベル**ドロップダウン メニューで、**関数**します。

    4.  **テーブル名** セクションで、作成するために使用する正確な名前を使用する必要があります、**テーブル**以前 (同じ大文字と小文字) などのサービスです。

    5.  内で、**ストレージ アカウント接続**セクションし、ドロップダウン メニューを使用して、そこから、ストレージ アカウントを選択します。 をクリックしない場合、**新規**と共に、ストレージ アカウントが表示されるはずのもう 1 つのパネルを表示する、セクション タイトルのハイパーリンクです。

        ![新しい記憶域](images/AzureLabs-Lab8-40.png)

15. クリックして**作成**設定が正常に更新されていることの通知が表示されます。

    ![関数を作成します。](images/AzureLabs-Lab8-41.png)

16. クリックすると**作成**関数のエディターにリダイレクトされます。

    ![関数コードを更新します。](images/AzureLabs-Lab8-42.png)

17. 関数エディター (関数のコードを置き換える) には、次のコードを挿入します。

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 含まれるライブラリを使用して、関数が受け取った移動されたオブジェクトの場所と名前、Unity シーンで (として、C#と呼ばれるオブジェクト**UnityGameObject**)。 このオブジェクトは、作成されたテーブル内のオブジェクトのパラメーターを更新する、使用されます。 次は、関数を作成した通知ハブ サービスにサブスクライブしているすべてのアプリケーションに通知する呼び出しを実行します。

18. コードの場所で、次のようにクリックします。**保存**します。

19. 次に、クリックして、 **\<** (矢印) アイコンをページの右側にあります。

    ![開いているアップロード パネル](images/AzureLabs-Lab8-43.png)

20. パネルは、右からにスライドします。 そのパネル で、**アップロード**、され、ファイル ブラウザーが表示されます。

21. 、に移動し、クリックすると、、 **project.json**ファイルで、で作成した**メモ帳**以前は、順にクリックします、**オープン**ボタンをクリックします。 このファイルは、関数が使用するライブラリを定義します。

    ![json をアップロードします。](images/AzureLabs-Lab8-44.png)

22. ファイルがアップロードされると、右側のパネルに表示されます。 内で開くをクリックすると、**関数**エディター。 表示する必要があります**まったく**(手順 23) の下の [次へ] のイメージと同じです。

23. その後、左側のパネルで、下にある**関数**、 をクリックして、**統合**リンク。

    ![関数を統合します。](images/AzureLabs-Lab8-45.png)

24. 画面右隅で、次のページで次のようにクリックします。**高度なエディター** (以下のとおり)。

    ![詳細エディターの起動](images/AzureLabs-Lab8-46.png)

25. A **function.json**ファイルは次のコード スニペットを置換する必要がある中央のパネルで開けません。 これは、関数を作成して、パラメーターを定義します。 関数に渡されます。

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. エディターは、次の図のようになります。

    ![標準のエディターに戻る](images/AzureLabs-Lab8-47.png)

27. 挿入した入力パラメーターは、テーブルおよびストレージの詳細一致しなくなり、お客様の情報に更新する必要がありますのでお気付きです。 **これは、ここは実行しないで**を次に説明しました。 クリックするだけで、**標準エディター**戻るには、ページの右上隅にあるリンクです。

28. 戻り、**標準エディター**、] をクリックして**Azure Table Storage (テーブル)** [**入力**します。 
    
    ![テーブルの入力](images/AzureLabs-Lab8-47-5.png)

29. 次の一致することを確認 **、** についてと異なる場合があります (は、イメージを次の手順を以下)。

    1.  **テーブル名**: Azure Storage、Table サービス内で作成したテーブルの名前。

    2.  **ストレージ アカウント接続:** クリックして**新しい**、と共にドロップダウン メニューで、表示されると、ウィンドウの右側にパネルが表示されます。

        ![新しい記憶域](images/AzureLabs-Lab8-48.png)

        1.  選択、**ストレージ アカウント**、ホストに先ほど作成した、**関数アプリです。**

        2. 表示になります、**ストレージ アカウント**接続値が作成されました。

        3. キーを押して確認**保存**が完了します。

    3.  **入力**ページに一致する必要があります、以下では、示す **、** 情報。

        ![入力を完了します。](images/AzureLabs-Lab8-49.png)

30. 次に、クリックして**Azure Notification Hub (通知)** -**出力**します。 次が一致することを確認 **、** についてと異なる場合があります (下図を次の手順がある)。

    1.  **通知ハブの名前**: これは、名前の**Notification Hub**以前に作成したサービス インスタンス。

    2.  **Notification Hubs の名前空間の接続**: クリックして**新しい**、と共にドロップダウン メニューに表示されます。

        ![出力を確認してください。](images/AzureLabs-Lab8-50.png)

    3. **接続**ポップアップが表示されます (下図を参照) を選択する必要がある、 **Namespace**の**Notification Hub**、以前に設定します。

    4. 選択、 **Notification Hub**中間のドロップダウン メニューから名前。

    5.  設定、**ポリシー**ドロップダウン メニューを**DefaultFullSharedAccessSignature**します。

    6. をクリックして、**選択**戻るボタンをクリックします。

        ![更新プログラムを出力します。](images/AzureLabs-Lab8-51.png)

31.  **出力**ページに一致する必要があります、以下では、ですが、 **、** 情報代わりにします。 キーを押して確認**保存**します。

> [!WARNING]
> *通知ハブの名前を直接編集しないでください*(する必要がありますすべてこれを使用して、**詳細エディター**正しく前の手順に従っていれば、します。

![完全な出力](images/AzureLabs-Lab8-50.png)

32. この時点では、動作していることを確認する、関数をテストする必要があります。 これには、次の手順を実行します。 

    1. もう一度、関数のページに移動します。

        ![完全な出力](images/AzureLabs-Lab8-50-1.png)

    2. 関数 ページで、戻る をクリックして、**テスト** タブを開くには、ページの一番右側にある、*テスト*ブレード。

        ![完全な出力](images/AzureLabs-Lab8-50-2.png)

    3. 内で、**要求本文**貼り付け ブレードのテキスト ボックスに、次のコード。

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. テストのコードの場所で、をクリックして、**実行**ボタン右、下で、テストが実行されます。 テストの出力ログは、関数コードの下のコンソール領域に表示されます。

        ![完全な出力](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 上記のテストに失敗した場合は設定が必要な二重チェックが正確には、上記の手順を実行したことを特に、内で、**パネルを統合**します。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第 7 章 – デスクトップの Unity プロジェクトの設定

> [!IMPORTANT]
> デスクトップ アプリケーションを作成するようになりました**されません**Unity エディターで作業します。 次の Visual Studio を使用して、アプリケーション (または、デプロイされたアプリケーション) の構成エディター以外では実行が必要です。 

次のコード例が Unity を使用した開発と複合現実は、一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

設定して、mixed reality イマーシブ ヘッドセットをテストします。

> [!NOTE] 
> **いない**このコースのモーションのコント ローラーが必要です。 イマーシブ ヘッドセットの設定のサポートが必要な場合に従ってくださいこの[Windows Mixed Reality を設定する方法についてのリンク](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。

1.  開いている**Unity**クリック**新規**します。

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-52.png)

2.  挿入、Unity プロジェクト名を指定する必要がある**UnityDesktopNotifHub**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![プロジェクトを作成します。](images/AzureLabs-Lab8-53.png)

3.  既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。 移動して**編集** > **設定**し、新しいウィンドウに移動**外部ツール**します。 変更 **External Script Editor** に **Visual Studio 2017** します。 閉じる、**設定**ウィンドウ。

    ![VS tools の外部セット](images/AzureLabs-Lab8-54.png)

4.  次に移動**ファイル** > **Build Settings**選択**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。

    ![プラットフォームを切り替える](images/AzureLabs-Lab8-55.png)

5.  **ファイル** > **Build Settings**、ことを確認します。

    1.  **デバイスを対象に**に設定されている**任意のデバイス**

        > このアプリケーションがありますが、デスクトップようにする必要があります**任意のデバイス**

    2.  **ビルドの種類**に設定されている**D3D**

    3.  **SDK**に設定されている**インストールされている最新**

    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**

    5.  **ビルドおよび実行**に設定されている**ローカル マシン**

    6.  ここでは、シーンを保存およびビルドに追加することをお勧めします。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![開いているシーンを追加します。](images/AzureLabs-Lab8-56.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![シーンの新しいフォルダー](images/AzureLabs-Lab8-57.png)

        3. 新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **NH\_デスクトップ\_シーン**、キーを押します**保存**します。

            ![新しい NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

6.  同じウィンドウをクリックして、**プレーヤー設定**ボタン領域に関連するパネルが開き、**インスペクター**が配置されています。

7.  このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **ランタイム バージョンをスクリプト**べき**試験的 (.NET 4.6 Equivalent)**

        2. **バックエンドの scripting**べき **.NET**

        3. **API の互換性レベル**べき **.NET 4.6**

            ![net 4.6 のバージョン](images/AzureLabs-Lab8-59.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**

            ![ティックのインターネット クライアント](images/AzureLabs-Lab8-60.png)

8.  戻り**Build Settings** *Unity C\#プロジェクト*が不要になったグレー; これの横にあるチェック ボックスをオンにします。

9.  閉じる、 **Build Settings**ウィンドウ。

10. シーンとプロジェクトを保存**ファイル** > **シーンを保存/ファイル** > **プロジェクトを保存**します。

    > [!IMPORTANT]
    > スキップする場合、 *Unity を設定する*このプロジェクト (デスクトップ アプリ) のコンポーネントのコードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)、としてプロジェクトにインポート、 [**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。  スクリプト コンポーネントを追加する必要があります。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第 8 章 - Unity で、Dll のインポート

Unity の Azure ストレージを使用する (それ自体を活用して、.Net SDK for Azure)。 詳細についてはこの後に[Unity 用の Azure Storage のリンク](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。

インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。 バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。

独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) GitHub から。 次に、次の操作を行います。

1.  追加、 **.unitypackage**に Unity を使用して、**資産\>パッケージのインポート\>カスタム パッケージ**メニュー オプション。

2.  **Unity パッケージのインポート**ポップアップ、選択できることの下のすべてのボックス * **プラグイン* \> * ストレージ * * *。  このコースの必要がないと、その他のすべてをオフにします。

    ![パッケージへのインポートします。](images/AzureLabs-Lab8-61.png)

3.  をクリックして、***インポート***をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、**ストレージ**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![任意のプラットフォームをオフにします。](images/AzureLabs-Lab8-62.png)

5.  *これら特定のプラグイン*選択すると、**をオフに** **Any プラットフォーム**と**をオフに** **WSAPlayer**クリックして**適用**します。

    ![プラットフォームの dll を適用します。](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Unity エディターでのみ使用するこれらの特定のプラグインをマークするされます。 WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。

6.  **ストレージ**プラグイン フォルダーのみを選択します。

    -   Microsoft.Data.Services.Client

        ![dll のセットを処理しません。](images/AzureLabs-Lab8-64.png)

7.  チェック、**しないプロセス**ボックス**プラットフォームの設定** をクリック***適用***します。

    ![処理は適用されません。](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 私たちはマークするこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。 このプラグインは処理されていない場合でも機能します。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>章 9 - デスクトップの Unity プロジェクトで TableToScene クラスを作成します。

このアプリケーションを実行するコードを含むスクリプトを作成する必要があります。

最初のスクリプトを作成する必要があるは**TableToScene**は責任を負います。

-   Azure テーブル内のエンティティを読み取っています。
-   テーブルのデータを使用して生成するには、オブジェクトを判別し、どの位置。

2 番目のスクリプトを作成する必要があるは**CloudScene**は責任を負います。

-   ユーザーが、シーンを基準としてオブジェクトをドラッグできるようにする、左クリック イベントを登録しています。
-   この Unity シーンからオブジェクト データをシリアル化し、Azure 関数アプリに送信します。

このクラスを作成します。

1.  右クリックし、**資産**フォルダーは、[プロジェクト] パネルにある**作成** > **フォルダー**します。 フォルダーの名前**スクリプト**します。

    ![scripts フォルダーを作成します。](images/AzureLabs-Lab8-66.png)

    ![2 の scripts フォルダーを作成します。](images/AzureLabs-Lab8-67.png)

2.  先ほど作成した、開くフォルダーをダブルクリックします。

3.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成** >   **C#スクリプト**。 スクリプトの名前**TableToScene**します。

    ![新しい c# スクリプト](images/AzureLabs-Lab8-68.png)
    ![TableToScene 名前の変更](images/AzureLabs-Lab8-69.png)

4.  Visual Studio 2017 で開くスクリプトをダブルクリックします。

5.  次の名前空間を追加します。

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  クラス内では、次の変数を挿入します。

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > 代替、 **accountName**を Azure ストレージ サービスの名前と値および**accountKey** (「次の図) Azure Portal で、Azure ストレージ サービスで見つかったキー値を持つ値。 
    >
    > ![アカウント キーのフェッチ](images/AzureLabs-Lab8-70.png)

7.  ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  内で、 **TableToScene**クラスでは、Azure テーブルから値を取得し、シーン内の適切なプリミティブを生成するために使用するメソッドを追加します。

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  外側、 **TableToScene**クラス、および逆シリアル化するアプリケーションによって使用されるクラスを定義する必要があります、**テーブル エンティティ**します。

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. 必ず**保存**Unity エディターに戻る前にします。

11. をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。

12. **スクリプト**フォルダーを開き、スクリプトを選択する**TableToScene ファイル**上にドラッグし、 **Main Camera**します。 結果は、以下のとおり。

    ![メイン カメラにスクリプトを追加します。](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>章 10 - デスクトップの Unity プロジェクトで CloudScene クラスを作成します。

2 番目のスクリプトを作成する必要があるは**CloudScene**は責任を負います。

-   ユーザーが、シーンを基準としてオブジェクトをドラッグできるようにする、左クリック イベントを登録しています。

-   この Unity シーンからオブジェクト データをシリアル化し、Azure 関数アプリに送信します。

2 番目のスクリプトを作成します。

1.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成**、 **C\#スクリプト**。 スクリプトの名前**CloudScene**
    
    ![新しい c# スクリプト](images/AzureLabs-Lab8-72.png)
    ![CloudScene の名前を変更](images/AzureLabs-Lab8-73.png)

2.  次の名前空間を追加します。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  代替、 **azureFunctionEndpoint** Azure 関数アプリの URL を次の図に示すように、Azure Portal で、Azure Function App サービスで見つかった値。

    ![関数の URL を取得します。](images/AzureLabs-Lab8-74.png)

5.  ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  内で、 **Update()** メソッド、ドラッグで、シーンの Gameobject を移動はさらに、マウス入力を検出する次のコードを追加します。 ユーザーがドラッグし、オブジェクトの削除された場合、そのメソッド名とオブジェクトの座標を渡すは**UpdateCloudScene()** 、Azure テーブルおよびトリガーを更新する Azure Function App サービスを呼び出すが、通知します。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  ここで追加、 **UpdateCloudScene()** 次に示すように、メソッド。

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  コードを保存し、Unity に戻る

9.  ドラッグ、 **CloudScene**にスクリプト、 **Main Camera**します。 

    1. をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。 

    2. **スクリプト**フォルダーを開き、選択、 **CloudScene**スクリプトを作成し、上にドラッグ、 **Main Camera**します。 結果は、以下のとおり。

        > ![クラウドのスクリプトをメイン カメラにドラッグします。](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第 11 章 – デスクトップ、UWP プロジェクトのビルド

このプロジェクトの Unity セクションに必要なものすべてが完了しましたようになりました。

1.  移動します**ビルド設定**(**ファイル** > **ビルド設定**)。

2.  **Build Settings**ウィンドウで、をクリックして**ビルド**します。

    ![プロジェクトをビルドします。](images/AzureLabs-Lab8-76.png)

3.  A**ファイル エクスプ ローラー**ビルドする場所の入力を求めるウィンドウがポップアップします。 新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。

    ![ビルド用の新しいフォルダー](images/AzureLabs-Lab8-77.png)

    1.  開き、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**NH\_デスクトップ\_アプリ**します。

        ![フォルダー名 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  **NH\_デスクトップ\_アプリ**選択します。 クリックして**フォルダーの選択**します。 プロジェクトは、ビルドを 1 分程度かかります。

4.  次のビルド、**ファイル エクスプ ローラー**新しいプロジェクトの場所が示されますが表示されます。 ただし、他を作成する必要があると Unity プロジェクトの最初に、次のいくつかの章を開くと、する必要はありません。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第 12 章 - 混合現実の Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている**Unity**クリック**新規**します。

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-79.png)

2.  Unity プロジェクト名を指定する必要がありますこれで挿入**UnityMRNotifHub**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![名前 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。 移動して**編集** > **設定**し、新しいウィンドウに移動**外部ツール**します。 変更 **External Script Editor** に **Visual Studio 2017** します。 閉じる、**設定**ウィンドウ。

    ![VS セット外部エディター](images/AzureLabs-Lab8-81.png)

4.  次に移動**ファイル** > **Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![UWP にプラットフォームを切り替える](images/AzureLabs-Lab8-82.png)

5.  移動して**ファイル** > **Build Settings**ことを確認してください。

    1.  **デバイスを対象に**に設定されている**任意のデバイス**

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2.  **ビルドの種類**に設定されている**D3D**

    3.  **SDK**に設定されている**インストールされている最新**

    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**

    5.  **ビルドおよび実行**に設定されている**ローカル マシン**

    6.  ここでは、シーンを保存およびビルドに追加することをお勧めします。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。

            ![開いているシーンを追加します。](images/AzureLabs-Lab8-83.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![シーンの新しいフォルダー](images/AzureLabs-Lab8-84.png)

        3. 新たに作成した開く**シーン**フォルダー、し、**ファイル名:** テキスト フィールドに「 **NH\_MR\_シーン**、キーを押します**保存**します。

            ![新しいシーン - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

6.  同じウィンドウをクリックして、**プレーヤー設定**ボタン領域に関連するパネルが開き、**インスペクター**が配置されています。    

    ![プレーヤー設定を開く](images/AzureLabs-Lab8-86.png)

7.  このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **ランタイム バージョンをスクリプト**べき**試験的**(.NET 4.6 Equivalent)
        2.  **バックエンドの scripting**べき ***.NET***
        3.  **API の互換性レベル**べき **.NET 4.6**

            ![api の互換性](images/AzureLabs-Lab8-87.png)

    2.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます

        ![xr の設定の更新](images/AzureLabs-Lab8-88.png)        

    3.  内で、**公開設定**] タブの [**機能**いったい。

        - **InternetClient**           

            ![ティックのインターネット クライアント](images/AzureLabs-Lab8-89.png)

8.  戻り**Build Settings**、 **UnityC#プロジェクト**が不要になったグレー: この横にあるチェック ボックスをオンにします。

9.  これらの変更完了ビルド設定ウィンドウを閉じます。

10. シーンとプロジェクトを保存**ファイル** > **シーンを保存/ファイル** > **プロジェクトを保存**します。

    > [!IMPORTANT]
    > スキップする場合、 *Unity を設定する*コンポーネント (複合現実アプリ)、このプロジェクトのコードにまっすぐコンティニュし、自由に[ダウンロードこの .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)、としてプロジェクトにインポート[**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)します。 スクリプト コンポーネントを追加する必要があります。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第 13 章 - 複合現実の Unity プロジェクトで、Dll のインポート

(Azure 用 .Net SDK を使用) する Unity ライブラリの Azure Storage が使用されます。 これに従ってください[Unity を使用した Azure Storage を使用する方法についてのリンク](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)します。
インポート後に再構成するプラグインを必要とする Unity での既知の問題は現在します。 バグが解決された後、次の手順 (このセクションでは 4 ~ 7) は必要に不要になった。

独自のプロジェクトに SDK をインポートすることを最新バージョンをダウンロードしていることを確認して[.unitypackage](https://aka.ms/azstorage-unitysdk)します。 次に、次の操作を行います。

1.  Unity を使用して、上記でダウンロードした .unitypackage を追加、**資産** > **パッケージのインポート** > **カスタム パッケージ**メニュー オプション.

2.  **Unity パッケージのインポート**ポップアップ、選択できることの下のすべてのボックス**プラグイン** > **ストレージ**します。

    ![パッケージのインポート](images/AzureLabs-Lab8-90.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、**ストレージ**の下のフォルダー**プラグイン**プロジェクトを表示し、次のプラグインを選択*のみ*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![プラグインを選択します。](images/AzureLabs-Lab8-91.png)

5.  *これら特定のプラグイン*選択すると、**をオフに** **Any プラットフォーム**と**をオフに** **WSAPlayer**クリックして**適用**します。

    ![プラットフォームの変更を適用します。](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Unity エディターでのみ使用するこれらの特定のプラグインをマークすることができます。 WSA フォルダー Unity からプロジェクトはエクスポート後に使用される同じプラグインのさまざまなバージョンがあるためにです。

6.  **ストレージ**プラグイン フォルダーのみを選択します。

    -   Microsoft.Data.Services.Client

        ![data services クライアントを選択します。](images/AzureLabs-Lab8-93.png)

7.  チェック、**しないプロセス**ボックス**プラットフォームの設定** をクリック**適用**します。

    ![処理はありません。](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > マークしているこのプラグイン「プロセスはありません」Unity アセンブリのパッチャがあるこのプラグインを処理できないのためです。 このプラグインは、処理されていない場合でも機能します。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第 14 章 – TableToScene クラスの複合現実の Unity プロジェクトの作成

**TableToScene**クラスで説明されているものと同じ[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。 同じクラスを作成で Unity プロジェクトの同様の手順が説明されている複合現実で[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)します。

この章では、両方が完了したら、 **Unity プロジェクト**このクラスの Main Camera を設定する必要があります。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第 15 章「Mixed Reality Unity プロジェクトで NotificationReceiver クラスを作成する

2 番目のスクリプトを作成する必要があるは**NotificationReceiver**は責任を負います。

-   アプリの初期化時、通知ハブに登録します。
-   通知ハブから通知をリッスンします。
-   受信した通知からオブジェクト データを逆シリアル化します。
-   逆シリアル化されたデータに基づく、シーン内の Gameobject に移動します。

作成する、 **NotificationReceiver**スクリプト。

1.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成**、 **C\#スクリプト**。 スクリプトの名前**NotificationReceiver**します。

    ![新しい c# スクリプト作成](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver という名前を付けます](images/AzureLabs-Lab8-96.png)

2.  これを開くためのスクリプトをダブルクリックします。

3.  次の名前空間を追加します。

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  次の変数を挿入します。

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  代替、 **hubName**を Notification Hubs サービス名に、値と**hubListenEndpoint**アクセス ポリシー タブで、Azure Notification Hubs のサービスで見つかったエンドポイント値と、Azure Portal (下図を参照してください)。

    ![通知ハブのポリシー エンドポイントを挿入します。](images/AzureLabs-Lab8-97.png)

6.  ここで追加、 **Start()** と**Awake()** クラスを初期化するメソッド。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  追加、 **WaitForNotification**アプリは、メイン スレッドと競合せず、通知ハブのライブラリからの通知を受信できるようにするメソッド。

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  次のメソッドでは、 **InitNotificationAsync()** 、通知ハブのサービスの初期化時にアプリケーションを登録します。 Unity では、プロジェクトをビルドできないため、コードをコメント アウトします。 Visual Studio で Azure メッセージング Nuget パッケージをインポートするときに、コメントが削除されます。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  次のハンドラー**チャネル\_PushNotificationReceived()** 通知が受信されるたびにトリガーされます。 デスクトップ アプリケーションに移動された Azure テーブル エンティティになるし、MR シーン内の同じ位置に対応する GameObject を移動すると、通知を逆シリアル化にされます。 
    
    > [!IMPORTANT]
    > コードは、Visual Studio 内で、Nuget パッケージ マネージャーを使用して、Unity プロジェクトをビルドした後は、追加、Azure メッセージング ライブラリを参照しているため、コードをコメント アウトします。 そのため、Unity プロジェクトされませんをビルドすることがコメント アウトされていない場合です。注意する必要があります、プロジェクトをビルドし、Unity に戻りたいが必要に**再びコメント化**コード。

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Unity エディターに戻る前に、変更を保存してください。

11. をクリックして、 **Main Camera**から、**階層** パネルにそのプロパティが表示されるように、**インスペクター**します。

12. **スクリプト**フォルダーを開き、選択、 **NotificationReceiver**スクリプトを作成し、上にドラッグ、 **Main Camera**します。 結果は、以下のとおり。

    ![カメラに通知の受信側のスクリプトをドラッグします。](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > これは、Microsoft HoloLens の開発は、更新する必要があります、 **Main Camera**の*カメラ*コンポーネント、ように。
    > - フラグをオフにします。純色
    > - 背景知識:黒

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第 16 章 – UWP への複合現実プロジェクトをビルド

この章では、ビルド前のプロジェクトのプロセスと同じです。 このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します**ビルド設定**(**ファイル** > **ビルド設定**)。

2.  **Build Settings** ] メニューの [確認**UnityC#プロジェクト*** がオンになって (これにより、ビルドの後に、このプロジェクト内のスクリプトを編集すること)。

3.  これが完了したら**ビルド**します。

    ![プロジェクトをビルドします。](images/AzureLabs-Lab8-99.png)

4.  A**ファイル エクスプ ローラー**ビルドする場所の入力を求めるウィンドウがポップアップします。 新しいフォルダーを作成 (をクリックして**新しいフォルダー**左上隅にある)、名前を付けます**ビルド**します。

    ![ビルド フォルダーを作成します。](images/AzureLabs-Lab8-100.png)

    1.  開き、新しい**ビルド**フォルダー、別のフォルダーを作成し、(を使用して**新しいフォルダー**もう一度)、名前を付けます**NH\_MR\_アプリ**します。

        ![NH_MR_Apps フォルダーを作成します。](images/AzureLabs-Lab8-101.png)

    2.  **NH\_MR\_アプリ**選択します。 クリックして**フォルダーの選択**します。 プロジェクトは、ビルドを 1 分程度かかります。

5.  次のビルド、**ファイル エクスプ ローラー**新しいプロジェクトの場所にウィンドウが開きます。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第 17 章 – UnityMRNotifHub ソリューションの NuGet パッケージの追加

> [!WARNING] 
> 次の NuGet パッケージを追加するに注意してください (次のコードをコメント解除します[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class))、コード、Unity プロジェクト内で再び開いたときにエラーが表示されます。 戻るし、Unity エディターで編集を続行する場合は、その errosome コードにコメントし、したら、Visual Studio に戻った後でもう一度コメント解除し、必要があります。 

複合現実のビルドが完了したら、ビルドした複合現実プロジェクトに移動し、Visual Studio 2017 でのソリューションを開くには、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックします。
追加する必要がありますこれで、 **WindowsAzure.Messaging.managed** NuGet パッケージです。 これは、通知ハブから通知を受信するために使用するライブラリ。

NuGet パッケージをインポートするには。

1.  **ソリューション エクスプ ローラー**ソリューションを右クリックして

2.  をクリックして**NuGet パッケージの管理**します。

    ![nuget マネージャーを開く](images/AzureLabs-Lab8-102.png)

3.  選択、***参照***タブし、検索**WindowsAzure.Messaging.managed**します。

    ![windows azure のメッセージング パッケージを検索します。](images/AzureLabs-Lab8-103.png)

4.  (次に示す) の結果を選択し、右側のウィンドウでに横にチェック ボックスをオン**プロジェクト**します。 ティックを横にチェック ボックスをオンに配置これは**プロジェクト**、横のチェック ボックスと共に、**アセンブリ CSharp**と**UnityMRNotifHub**プロジェクト。

    ![すべてのプロジェクトをオンに](images/AzureLabs-Lab8-104.png)

5.  最初に指定されたバージョン**可能性がある**このプロジェクトを互換性があります。 そのため、次に、ドロップダウン メニューをクリックします**バージョン**、 をクリック**バージョン 0.1.7.9**、 をクリックし、**インストール**します。

6.  NuGet パッケージのインストールが終了したようになりました。 入力したコメントが付けられたコードの検索、 **NotificationReceiver**クラスし、コメントを削除する.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第 18 章 - 編集 UnityMRNotifHub アプリケーション、NotificationReceiver クラス

次の追加した後、 **NuGet パッケージの**、する必要があります*をコメント解除します*内のコードの一部、 **NotificationReceiver**クラス。

たとえば、次のようなアニメーションや効果を作成できます。

1. 上部にある名前空間:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. 内のすべてのコード、 **InitNotificationsAsync()** メソッド。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 上記のコードにコメントを持つ: が誤っていることを確認*コメント解除された*(ように、コードはコンパイルされませんがあれば!) をコメントします。

3. 最後に、 **Channel_PushNotificationReceived**イベント。

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

このコンピューターでは、保存、および、し、[次へ] の章に進むことを確認してください。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第 19 章 – ストア アプリに複合現実プロジェクトに関連付ける

これで、関連付ける必要があります、**複合現実**ラボの開始時に作成したストア アプリにプロジェクト。

1.  ソリューションを開きます。

2.  ソリューション エクスプ ローラー パネルで、移動先の UWP アプリ プロジェクトを右クリックして**ストア**、および**アプリケーションをストアと関連付ける.** .

    ![ストアのアソシエーションを開く](images/AzureLabs-Lab8-105.png)

3.  新しいウィンドウが呼び出された表示**アプリケーションを Windows ストアと関連付ける**します。 **[次へ]** をクリックします。

    ![次の画面に移動します。](images/AzureLabs-Lab8-106.png)

4.  ログインしたら、アカウントに関連付けられているすべてのアプリケーションを構成が読み込まれます。 場合は、アカウントにログインしていない、**ログで**このページでします。

5.  検索、**ストアのアプリ名**このチュートリアルの開始時に作成してそれを選択します。 **[次へ]** をクリックします。

    ![検索して、ストアの名前を選択します。](images/AzureLabs-Lab8-107.png)

6.  クリックして**関連付ける**します。

    ![アプリを関連付ける](images/AzureLabs-Lab8-108.png)

7.  これで、アプリは**関連付けられている**ストア アプリを使用します。 これは、通知を有効にする必要があります。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第 20 章 - UnityMRNotifHub と UnityDesktopNotifHub アプリケーションの展開

この章は、実行中のアプリ、デスクトップ コンピューターで実行する 1 台の両方と、イマーシブ ヘッドセット内で、その他の結果が含まれますと 2 人のユーザーで、簡単に場合があります。

イマーシブ ヘッドセット アプリは、シーン (ローカルの Gameobject の位置変更) に変更を受信を待機しているし、ローカル シーン (位置変更)、MR アプリに共有されますが、デスクトップ アプリが変更を加えています。 理にかなって MR アプリのデプロイを最初に、デスクトップ アプリは、後に、受信側がリッスンを開始することができるようにします。

展開する、 **UnityMRNotifHub**ローカル コンピューター上のアプリ。

1.  ソリューション ファイルを開き、 **UnityMRNotifHub**でアプリ**Visual Studio 2017**します。

2.  **ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。

3.  **ソリューション構成**選択**デバッグ**します。

    ![セットのプロジェクトの構成](images/AzureLabs-Lab8-109.png)

4.  移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。

5.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。

展開する、 **UnityDesktopNotifHub**ローカル コンピューター上のアプリ。

1.  ソリューション ファイルを開き、 **UnityDesktopNotifHub**でアプリ**Visual Studio 2017**します。

2.  **ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。

3.  **ソリューション構成**選択**デバッグ**します。

    ![セットのプロジェクトの構成](images/AzureLabs-Lab8-110.png)

4.  移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。

5.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。

6.  複合現実アプリケーション、デスクトップ アプリケーションを起動します。

実行されている両方のアプリケーションは、デスクトップに (左マウス ボタンを使用して) シーンのオブジェクトを移動します。 これらの位置変更はローカルでできるし、シリアル化すると、Function App サービスに送信します。 そうすると、Function App サービスでは、通知ハブと共にテーブルが更新されます。 更新プログラムを受信すると、通知ハブは、更新されたデータに直接送信する受信のデータを逆シリアル化し、新しい位置指定データをローカルのオブジェクトに適用、(この場合は、イマーシブ ヘッドセット アプリ) をすべての登録済みアプリケーションシーン内に移動します。


## <a name="your-finished-your-azure-notification-hubs-application"></a>Azure Notification Hubs アプリケーションの終了
 
これで、Azure Notification Hubs のサービスを活用し、アプリ間の通信を許可する mixed reality アプリを構築します。
 
![最終的な製品-終了](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

Gameobject の色を変更し、シーンを表示するその他のアプリに通知を送信する方法を操作することができますか。

### <a name="exercise-2"></a>手順 2

Gameobject の動きを MR アプリに追加し、デスクトップ アプリの更新されたシーンを参照してくださいか。
