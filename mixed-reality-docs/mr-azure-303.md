---
title: MR と Azure 303 の自然言語の理解 (LUIS)
description: このコースでは、複合現実のアプリケーション内で Azure Language Understanding Intelligence Service (LUIS) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality, academy、unity、チュートリアル、api、language understanding インテリジェンス サービス, luis、hololens、没入型、vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603074"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR と Azure 303:自然言語の理解 (LUIS)

このコースでは、Language Understanding API を使用した Azure Cognitive Services を使用して、複合現実のアプリケーションに言語理解機能を統合する方法を学びます。

![ラボの結果](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* にどのような人が必要で、ユーザーの声の抽出をユーザー入力からの意味を確保できるアプリケーションを提供する Microsoft Azure サービスです。 これを実現するには、機械学習を理解および入力の情報では、学習し、関連する詳細な情報に応答できます。 詳細については、次を参照してください。、 [Azure Language Understanding (LUIS) ページ](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)します。

このコースを完了すると、以下を実行できる必要が複合現実イマーシブ ヘッドセット アプリケーションが完成します。

1.  イマーシブ ヘッドセットにアタッチされているマイクを使用して、ユーザーの入力音声をキャプチャします。 
2.  キャプチャされたディクテーションの送信、 *Azure Language Understanding Intelligent Service* (*LUIS*)。 
3.  LUIS の抽出、分析され、ユーザーの要求の目的が行われるかを判断しようとする情報送信から意味があります。

開発では、ユーザーを使用して、音声または視線、サイズと、シーン内のオブジェクトの色を変更することが、アプリの作成が含まれます。 アニメーション コント ローラーの使用は扱いません。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

複数回が LUIS をトレーニングする準備が、これは、「[第 12 章](#chapter-12--improving-your-luis-service)します。 LUIS がトレーニングされている詳細度より良い結果が得られます。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR と Azure 303:自然言語の理解 (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースが主に Windows Mixed Reality 没入型 (VR) ヘッドセットを重点的に Microsoft HoloLens には、このコースで学習する内容を適用することもできます。 コースを実行するとき、HoloLens をサポートするために必要な場合があります変更でノートが表示されます。 HoloLens を使用する場合は、音声キャプチャ中にいくつかのエコーが気付きです。

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
- (ヘッドセットには、組み込みのマイクとスピーカーを持っていない) 場合は、内蔵マイクでヘッドフォン
- Azure のセットアップおよび LUIS 取得するためのインターネット アクセス

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。 
2.  ディクテーションを有効にするためにコンピューターを許可するには**Windows の設定 > プライバシーに関する > 読み上げ、手描き入力機能 (&) を入力する** ボタンを押すと**音声サービスをオンにして、入力候補**します。
3.  このチュートリアルでは、コードから記録することにより、**マイク デバイスの既定の**コンピューターに設定します。 マイクの既定のデバイスが音声のキャプチャに使用する 1 つとして設定することを確認します。
4.  ヘッドセットに内蔵マイクがある場合は、必ずオプション *「マイ ヘッドセットを着用するときに切り替えるヘッドセット マイク」* でオンに、 *Mixed Reality ポータル*設定します。

    ![イマーシブ ヘッドセットの設定](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第 1 章 – Azure Portal のセットアップ

使用する、 *Language Understanding*サービス、Azure でアプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  [Azure ポータル](https://portal.azure.com) にログインします。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**新規**左上隅にある検索して*Language Understanding*、 をクリック**Enter**します。 

    ![LUIS のリソースを作成します。](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 単語**新規**に置き換えられました**リソースの作成**、新しいポータルでします。
 
3.  右側に新しいページは、Language Understanding サービスの説明を提供します。 このページの左下にある at、**作成**ボタンは、このサービスのインスタンスを作成します。

    ![LUIS サービスの作成 - 法的通知](images/AzureLabs-Lab3-02.png)
 
4.  作成した 1 回。

    1. 必要な挿入**名前**このサービス インスタンス。
    2. 選択、**サブスクリプション**します。
    3. 選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *LUIS サービス*、(F0 という名前)、free レベルを使用することがあります。 無料の割り当ては、このコースのための十分な複数の必要があります。
    4. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 

        > 詳細にする場合、Azure リソース グループについてのご[リソース グループの記事を参照してください。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)します。

    5. 確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。
    6. また、このサービスに適用される条件を理解したことを確認する必要があります。
    7. **[作成]** を選択します。

        ![LUIS サービス - ユーザー入力を作成します。](images/AzureLabs-Lab3-03.png)
 
5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。
6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。 
 
    ![新しい Azure の通知の画像](images/AzureLabs-Lab3-04.png)

7.  新しいサービス インスタンスを探索する通知をクリックします。

    ![成功したリソースの作成の通知](images/AzureLabs-Lab3-05.png)
 
8.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 新しい LUIS サービス インスタンスに表示されます。 
 
    ![LUIS のキーにアクセスします。](images/AzureLabs-Lab3-06.png)

9.  このチュートリアルでは、内でアプリケーションがサービスのサブスクリプション キーを使用して、これは、サービスへの呼び出しを実行する必要があります。
10. *クイック スタート* ページの*LUIS API*サービスは、最初のステップに移動し、*キーを取得する*、 をクリック**キー** (することもできますこれは実現キー アイコンによって示される、サービスのナビゲーション メニューにある青いハイパーリンク キーをクリックして)。 これが明らかに、サービス*キー*します。
11. このプロジェクトの後半で必要になるため、表示されているキーの 1 つのコピーを実行します。 
12. *サービス* ページで、をクリックして*Language Understanding ポータル*に LUIS アプリ内で、新しいサービスの作成に使用する web ページにリダイレクトされます。 

## <a name="chapter-2--the-language-understanding-portal"></a>第 2 章 –、Language Understanding ポータル

このセクションでは、LUIS ポータルに LUIS アプリを作成する方法を学習します。 

> [!IMPORTANT]
> わけを設定する、*エンティティ*、*インテント*、および*発話*この章では、LUIS サービスの構築の最初の手順のみ: にも必要になりますサービスの再トレーニング、何回かためより正確にします。 については、サービスの再トレーニング、[最後の章](#chapter-12--improving-your-luis-service)のこのコースでは、これを完了するようにします。

1.  達すると、 *Language Understanding ポータル*、ない場合に、既に、Azure portal と同じ資格情報でログインする必要があります。 

    ![LUIS のログイン ページ](images/AzureLabs-Lab3-07.png)
 
2.  これは、LUIS を使用して、最初に、検索 をクリックして、ウェルカム ページの一番下までスクロールする必要があります、**作成 LUIS アプリ**ボタンをクリックします。

    ![LUIS アプリのページを作成します。](images/AzureLabs-Lab3-08.png)
 
3.  ログインすると、クリックして**のマイ アプリ**(ない場合そのセクションでは現在)。 クリックし、**新しいアプリの作成**です。

    ![LUIS のマイ アプリのイメージ](images/AzureLabs-Lab3-09.png)
 
4.  アプリを指定する*名前*します。
5.  変更する必要がある場合は、アプリは、英語以外の言語を理解することになって、*カルチャ*適切な言語です。
6.  ここで追加することも、*説明*新しい LUIS アプリの。

    ![LUIS - 新しいアプリを作成します。](images/AzureLabs-Lab3-10.png)

7.  キーを押すと**完了**、入力する、*ビルド*の新しいページ*LUIS*アプリケーション。
8.  ここで理解するいくつかの重要な概念があります。

    -   *インテント*、次のクエリをユーザーから呼び出されるメソッドを表します。 *インテント*1 つまたは複数あります*エンティティ*します。
    -   *エンティティ*、関連する情報を示すクエリのコンポーネントである、*インテント*します。
    -   *発話*クエリの例については、開発者でその LUIS が自体のトレーニングに使用されます。

これらの概念が完全がない場合は、クリア、問題なく、このコースはこの章でさらにそれらを明確です。

作成は、まず、*エンティティ*このコースを構築するために必要です。

9.  ページの左側にある、] をクリックして*エンティティ*の [**新しいエンティティを作成**です。

    ![新しいエンティティを作成します。](images/AzureLabs-Lab3-11.png)

10. 新しいエンティティを呼び出す*色*、その型に設定*単純*、キーを押します**完了**します。

    ![色の単純なエンティティを作成します。](images/AzureLabs-Lab3-12.png)
 
11. 3 個以上単純なエンティティという名前を作成するには、このプロセスを繰り返します。

    -   *upsize*
    -   *downsize*
    -   *ターゲット*

結果は、次の図のようになります。

![エンティティの作成の結果](images/AzureLabs-Lab3-13.png)
 
作成を開始する時点でこの*インテント*します。 

> [!WARNING]
> 削除しないでください、 **None**インテントです。

12. ページの左側にある、 をクリックして**インテント**、をクリックして**新しいインテント作成**です。

    ![新しいインテントを作成します。](images/AzureLabs-Lab3-14.png)

13. 新しい*インテント* **ChangeObjectColor**します。

    > [!IMPORTANT]
    > これは、*インテント*名が使用されるこのコースの後半で、コード内でそのため最良の結果を使用して、この名前指定されたとおりです。

インテント ページに表示される名前のことを確認します。

![LUIS のインテント ページ](images/AzureLabs-Lab3-15.png)

5 個以上の異なる型に求めるテキスト ボックスがあることがわかります*発話*します。

> [!NOTE]
> LUIS では、すべての発話を小文字に変換します。

14. 次を挿入します*発話*上部のテキスト ボックスに (テキストと現在 *... 約 5 の例の型* )、キーを押します**Enter**:

```
The color of the cylinder must be red
```

その新しい*発話*の下に一覧に表示されます。

次の同じプロセスでは、次の 6 発話を挿入します。

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

作成したそれぞれの発話エンティティとして LUIS がどの単語を使用する必要がありますを指定する必要があります。 この例では、としてすべての色のラベルを付ける必要があります、*色*エンティティ、および可能なすべての参照をターゲットとして、*ターゲット*エンティティ。

15. これを行うには、という語をクリックを再試行してください*円柱*でクリックし、最初の発話*ターゲット*します。

    ![発話のターゲットを特定します。](images/AzureLabs-Lab3-16.png)
 
16. ここで単語をクリックして*赤い*でクリックし、最初の発話*色*。

    ![発話のエンティティを識別します。](images/AzureLabs-Lab3-17.png)
 
17. また、次の行のラベルを付ける場所*キューブ*する必要があります、*ターゲット*と*黒い*する必要があります、*色*します。 単語の使用も注意してください。 *'this'*、 *'it'*、と *'オブジェクト'*、提供しています、これも使用できる非固有のターゲット型にします。 

18. 上記のプロセスを繰り返して、すべての発話にというラベルが付いたエンティティが存在します。 参照してください、次の画像が必要な場合。

    > [!TIP]
    > ときに、それらのエンティティとしてラベル付けに単語を選択します。
    > - 1 つの単語だけをクリックします。
    > - 一連の 2 つ以上の単語の先頭にしてから、セットの末尾でをクリックします。

    > [!NOTE]
    > 使用することができます、*トークン ビュー*を切り替えるトグル ボタン**エンティティ/トークン ビュー**!

19. 結果は、次の画像に示すように、表示する必要があります、**エンティティ/トークン ビュー**:

    ![エンティティのビュー (&)、トークン](images/AzureLabs-Lab3-18.png)
  
20. この時点でキーを押して、**トレーニング**ページの右上にあるボタンをクリックし、緑を有効にする上で小さな丸いインジケーターを待機します。 これは、この目的を認識する LUIS が正常にトレーニングされていることを示します。

    ![LUIS をトレーニング](images/AzureLabs-Lab3-19.png)
 
21. 演習として作成すると呼ばれる新しい目的**ChangeObjectSize**、エンティティを使用して*ターゲット*、*アップサイズ*、および*ダウンサイズ*します。
22. 次の以前のインテントと同じプロセスの次の 8 (8) 発話を挿入*サイズ*を変更します。

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 結果は、次の図に示すようにする必要があります。

    ![ChangeObjectSize トークンのセットアップ/エンティティ](images/AzureLabs-Lab3-20.png) 

24. 両方のインテント、1 回**ChangeObjectColor**と**ChangeObjectSize**作成されているし、トレーニングをクリックして、**発行**ページ上部にあるボタンをクリックします。

    ![LUIS サービスを発行します。](images/AzureLabs-Lab3-21.png)

25. *発行*ページの最終処理して、コードでアクセスできるように、LUIS アプリを発行します。

    1. セットをスケール ダウン、ドロップ*Publish To*として**運用**します。
    2. 設定、*タイムゾーン*タイム ゾーンにします。
    3. チェック ボックスをオン**すべて含む予測スコアのインテント**します。
    4. をクリックして**運用スロットに発行**します。

        ![発行の設定](images/AzureLabs-Lab3-22.png)

26. セクションで*リソースとキー*:

    1.  Azure Portal でのサービス インスタンスに設定するリージョンを選択します。
    2.  表示されます、 **Starter_Key** 、下の要素を無視します。
    3.  をクリックして**キーの追加**を挿入し、*キー*サービス インスタンスを作成したときに、Azure Portal で取得しました。 ドロップダウン メニューを指定した場合は、Azure と LUIS ポータルは、同じユーザーにログインしている、*テナント名*、*サブスクリプション名*、および*キー* (を使用します。Azure Portal で以前に指定したように、同じ名前になります。

    > [!IMPORTANT] 
    > 下に*エンドポイント*キーに対応するエンドポイントのコピーを挿入した、コードですぐに使用されます。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第 3 章 – Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab3-24.png)

2.  Unity プロジェクト名を指定する必要がありますこれで挿入**MR_LUIS**します。 必ず、プロジェクトの種類に設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![新しい Unity プロジェクトの詳細を提供します。](images/AzureLabs-Lab3-25.png)
 
3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 編集 > 設定し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![スクリプト エディターの基本設定を更新します。](images/AzureLabs-Lab3-26.png)
 
4.  次に移動**ファイル > Build Settings**にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**、 をクリックして、**プラットフォームの切り替え**ボタンをクリックします。

    ![[設定] ウィンドウ切り替え UWP プラットフォームをビルドします。](images/AzureLabs-Lab3-27.png)
 
5.  移動して**ファイル > Build Settings**ことを確認してください。

    1. **デバイスを対象に**に設定されている**任意のデバイス**

        > Microsoft HoloLens、設定**ターゲット デバイス**に*HoloLens*します。

    2. **ビルドの種類**に設定されている**D3D**
    3. **SDK**に設定されている**インストールされている最新**
    4. **Visual Studio バージョン**に設定されている**インストールされている最新**
    5. **ビルドおよび実行**に設定されている**ローカル マシン**
    6. シーンを保存し、ビルドに追加します。

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。
        
            ![開いているシーン ボタンの追加 をクリック](images/AzureLabs-Lab3-28.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

            ![新しいスクリプト フォルダーを作成します。](images/AzureLabs-Lab3-29.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **MR_LuisScene**、キーを押します**保存します**。

            ![シーンの新しい名前を付けます。](images/AzureLabs-Lab3-30.png)

    7. 設定に残っている*Build Settings*、ここでは既定値として残しておく必要があります。

6. *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![プレーヤー設定を開きます。](images/AzureLabs-Lab3-31.png) 
 
7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1. **ランタイム バージョンをスクリプト**する必要があります**安定した**(.NET 3.5 相当)。
        2. **バックエンドの scripting**べき **.NET**
        3. **API の互換性レベル**べき **.NET 4.6**

            ![その他の設定を更新します。](images/AzureLabs-Lab3-32.png)
      
    2. 内で、**発行の設定**] タブの [**機能**、確認してください。

        1. **InternetClient**
        2. **マイク**

            ![発行の設定を更新しています。](images/AzureLabs-Lab3-33.png)

    3. パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![X の R の設定を更新します。](images/AzureLabs-Lab3-34.png)

8.  戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。 
9.  ビルド設定ウィンドウを閉じます。
10. シーンとプロジェクトを保存 (**ファイル > シーン保存/ファイル > プロジェクトを保存**)。

## <a name="chapter-4--create-the-scene"></a>第 4 章 – シーンを作成します。

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)、としてプロジェクトにインポート、[カスタム パッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 5 章](#chapter-5--create-the-microphonemanager-class)します。 

1.  空の領域で右クリックし、*階層パネル* **3D オブジェクト**、追加、**平面**します。

    ![平面を作成します。](images/AzureLabs-Lab3-35.png)

2.  注意を内で右クリックすると、*階層*もう一度選択されている最後のオブジェクトがある場合は、複数のオブジェクトを作成、選択したオブジェクトをする、新しいオブジェクトの親。 階層内の空白領域をクリックし、右クリックし、この問題を回避します。

3.  次のオブジェクトを追加する上記の手順を繰り返します。

    1. *球*
    2. *円柱*
    3. *Cube*
    4. *3D テキスト*

4.  結果として得られるシーン*階層*次の図のようになります。

    ![シーン階層の設定。](images/AzureLabs-Lab3-36.png)
 
5.  左クリックしてで、 **Main Camera**ことを選択するために見て、*インスペクター パネル*すべて Camera オブジェクトが表示されます、そのコンポーネント。
6.  をクリックして、**コンポーネントの追加**の一番下にあるボタン、*インスペクター パネル*します。

    ![オーディオ ソースを追加します。](images/AzureLabs-Lab3-37.png)
 
7.  呼ばれるコンポーネントの検索*オーディオ ソース*の上に示すようにします。
8.  確認、*変換*Main Camera のコンポーネント (0,0,0) に設定されて、これを行うキーを押して、**歯車**カメラの横にあるアイコン*変換*コンポーネント選択と**リセット**します。 *変換*し、コンポーネントのようになります。

    1.  *位置*に設定されている**0, 0, 0**します。
    2.  *回転*に設定されている**0, 0, 0**します。

    > [!NOTE] 
    > Microsoft HoloLens のも、次を変更する必要がありますに含まれています、**カメラ**このコンポーネントでは、 **Main Camera**:
    > - **フラグをオフにします。** 純色です。
    > - **バック グラウンド**' 黒、アルファ 0' – 16 進カラー: #00000000 します。

9.  左クリックしてで、**平面**をオンにします。 *インスペクター パネル*設定、*変換*コンポーネントを次の値。

    |       | 変換 -*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. 左クリックしてで、**球**をオンにします。 *インスペクター パネル*設定、*変換*コンポーネントを次の値。

    |       | 変換 -*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. 左クリックしてで、**円柱**をオンにします。 *インスペクター パネル*設定、*変換*コンポーネントを次の値。

    |       | 変換 -*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. 左クリックしてで、**キューブ**をオンにします。 *インスペクター パネル*設定、*変換*コンポーネントを次の値。

    |        | 変換 -*位置* |       |  \| |       | 変換 -*回転* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 左クリックしてで、**新しいテキスト**オブジェクトを選択します。 *インスペクター パネル*設定、*変換*コンポーネントを次の値。

    |       | 変換 -*位置* |       |  \| |       | 変換 -*スケール* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 変更**フォント サイズ**で、**テキスト メッシュ**コンポーネントを**50**します。
15. 変更、*名前*の**テキスト メッシュ**オブジェクトを**テキストのディクテーション**します。

    ![3D テキスト オブジェクトを作成します。](images/AzureLabs-Lab3-38.png)
 
16. パネルの階層構造は、次のようになります。

    ![テキストは、シーン ビューでメッシュします。](images/AzureLabs-Lab3-38b.png)


17. 最終的なシーンは、次の図のようになります。

    ![シーンのビュー。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第 5 章 – MicrophoneManager クラスを作成します。

最初のスクリプトを作成するには、 *MicrophoneManager*クラス。 次に、作成、 *LuisManager*、*ビヘイビアー*クラス、最後に、*視線*クラス (自由と説明がここでは、これらすべてを作成するには各章に到達) します。

*MicrophoneManager*クラスは責任を負います。

-   ヘッドセットまたは (方は、既定のものです) のマシンにアタッチされた録音デバイスを検出します。
-   音声 (音声) を使用すると、キャプチャし、ディクテーションを使用して、文字列として保存します。
-   音声が一時停止すると後でディクテーションを送信、 *LuisManager*クラス。 

このクラスを作成します。 

1.  右クリックし、*プロジェクト パネル*、**作成 > フォルダー**します。 フォルダーを呼び出す**スクリプト**します。 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab3-40.png)
 
2.  **スクリプト**フォルダーが作成されるをダブルクリックして開きます。 その後、そのフォルダー内で右クリックし、**作成 >C#スクリプト**します。 スクリプトの名前*MicrophoneManager*します。 

3.  ダブルクリックします。 *MicrophoneManager*ファイルを開く*Visual Studio*します。
4.  ファイルの先頭には、次の名前空間を追加します。

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  内で、次の変数を追加し、 *MicrophoneManager*クラス。

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  コードを*Awake()* と*Start()* 今すぐメソッドを追加する必要があります。 これらが、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  メソッドに渡すの開始し、音声のキャプチャを停止する、アプリが使用する必要があります、 *LuisManager*クラスと、すぐにビルドします。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  追加、*ディクテーション ハンドラー*ですが、音声を置いたときに呼び出されます。 このメソッドは合格するテキストをディクテーション、 *LuisManager*クラス。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 削除、 *Update()* メソッドのため、このクラスは使用されません。

9.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

    > [!NOTE]
    > この時点で表示されるエラーが表示されます、 *Unity エディターのコンソール パネル*します。 これは、コードを参照しているため、 *LuisManager*クラスは次の章で作成されます。

## <a name="chapter-6--create-the-luismanager-class"></a>第 6 章 – LUISManager クラスを作成します。

作成するための時間は、 *LuisManager*クラスは、Azure LUIS サービスへの呼び出しになります。 

このクラスの目的からテキストをディクテーションを受信する、 *MicrophoneManager*クラスし、送信、 *Azure Language Understanding API*分析します。

このクラスが逆シリアル化、 *JSON*応答の適切なメソッドを呼び出すと、*ビヘイビアー*クラス アクションをトリガーします。

このクラスを作成します。 

1.  ダブルクリック、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前*LuisManager*します。 
3.  Visual Studio で開くことをスクリプトをダブルクリックします。
4.  ファイルの先頭には、次の名前空間を追加します。

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  3 つのクラスを作成して開始する**内**、 *LuisManager*クラス (に同じスクリプト ファイル内の上、 *Start()* メソッド) を表す、逆シリアル化されました。Azure からの JSON 応答です。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  次に、内部では、次の変数を追加、 *LuisManager*クラス。
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  で LUIS エンドポイントを今すぐ配置してください (これは、LUIS ポータルから必要があります)。

8.  コードを*Awake()* メソッドは今すぐ追加する必要があります。 このメソッドが、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  このアプリケーションは、送信から受信したディクテーションに使用する方法を作成する必要があるので、 *MicrophoneManager*クラスを*LUIS*、受信して、応答を逆シリアル化します。 
10. インスタンスに渡される目的、および関連付けられているエンティティは、の値が決まると、*ビヘイビアー*目的のアクションをトリガーするクラス。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. という新しいメソッドを作成する*AnalyseResponseElements()* 、その結果を読み取ることが*AnalysedQuery*し、エンティティを決定します。 これらのエンティティが決まったらのインスタンスに渡されます、*ビヘイビアー*アクションで使用するクラス。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 削除、 *Start()* と*Update()* メソッドをこのクラスはそれらを使用しないためです。

12. 変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

> [!NOTE]
> 表示されているいくつかのエラーが表示されますこの時点で、 *Unity エディターのコンソール パネル*します。 これは、コードを参照しているため、*ビヘイビアー*クラスは次の章で作成されます。

## <a name="chapter-7--create-the-behaviours-class"></a>第 7 章 – 動作クラスを作成します。

*ビヘイビアー*クラスによって提供されるエンティティを使用してアクションをトリガーする、 *LuisManager*クラス。

このクラスを作成します。 

1.  ダブルクリック、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前*ビヘイビアー*します。 
3.  ファイルを開くスクリプトをダブルクリックします。 *Visual Studio*します。
4.  内で、次の変数を追加し、*ビヘイビアー*クラス。

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  追加、 *Awake()* メソッドのコード。 このメソッドが、クラスの初期化時に呼び出されます。

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  によって、次のメソッドが呼び出される、 *LuisManager*オブジェクトが、クエリの対象であることを確認し、適切なアクションをトリガーして (これは、先ほど作成した) クラス。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  追加、 *FindTarget()* メソッドの判断するために、 *GameObjects*目的は、現在のターゲットであります。 このメソッドの既定値をターゲット、 *GameObject*される"gazed"エンティティの明示的なターゲットが定義されていない場合。

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 削除、 *Start()* と*Update()* メソッドをこのクラスはそれらを使用しないためです。

8.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-8--create-the-gaze-class"></a>章 – 8 視線の先クラスを作成します。

このアプリを完了する必要がある最後のクラスは、*視線*クラス。 このクラスへの参照を更新する、 *GameObject*現在のユーザーのビジュアル フォーカスします。

このクラスを作成します。 

1.  ダブルクリック、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前*視線*します。 
3.  ファイルを開くスクリプトをダブルクリックします。 *Visual Studio*します。
4.  このクラスに次のコードを挿入します。

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-9--completing-the-scene-setup"></a>第 9 章 – シーンのセットアップの完了

1.  シーンのセットアップを完了するには、Scripts フォルダーから作成した各スクリプトをドラッグして、 **Main Camera**オブジェクト、*階層パネル*します。
2.  選択、 **Main Camera**を見て、*インスペクター パネル*、アタッチした各スクリプトに表示できるし、まだ設定している各スクリプトにパラメーターがあることがわかります。

    ![カメラの参照のターゲットを設定します。](images/AzureLabs-Lab3-41.png)

3.  これらのパラメーターを正しく設定するには、次の手順を実行します。

    1. *MicrophoneManager*:

        - *階層パネル*、ドラッグ、**テキストのディクテーション**オブジェクトを**ディクテーション テキスト**パラメーター値のボックスです。

    2. *ビヘイビアー*から、*階層パネル*:

        - ドラッグ、**球**オブジェクトを*球*参照ターゲット ボックス。
        - ドラッグ、**円柱**に、*円柱*参照ターゲット ボックス。
        - ドラッグ、**キューブ**に、*キューブ*参照ターゲット ボックス。

    3. *視線*:

        - 設定、*最大距離の視線*に**300** (されていない) 場合。 

4.  結果は、次の図のようになります。

    ![設定、カメラの参照のターゲットを表示するようになりました。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第 10 章 – Unity エディターでのテスト

シーンのセットアップを正しく実装することをテストします。

次のことを確認してください。

-   関連付けられているすべてのスクリプト、 **Main Camera**オブジェクト。 
-   内のすべてのフィールド、*カメラ インスペクター [メイン] パネル*が適切に割り当てられます。

1.  キーを押して、**再生**ボタン、 *Unity エディター*します。 アプリは、添付のイマーシブ ヘッドセット内で実行する必要があります。

2.  など、いくつかの発話を試してください。

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 変更する既定のオーディオ デバイスについて、Unity コンソールで、エラーが発生した場合期待どおりにシーンが機能しない可能性があります。 これは、複合現実ポータルが設定されているヘッドセットの組み込みのマイクを扱う方法に起因します。 このエラーを参照してください、単にシーンを停止、再開し、として動作する必要がありますが必要です。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第 11 章 – ビルドおよびサイドロード UWP ソリューション

アプリケーションが Unity エディターでの作業でことを確認して後、は、構築およびデプロイする準備が完了したら。

作成する方法。

1.  現在のシーンを保存 をクリックして**ファイル > 保存**します。
2.  移動して**ファイル > のビルド設定**します。
3.  というボックスをオンに**UnityC#プロジェクト**(が表示されると、UWP プロジェクトが作成されると、コードのデバッグに便利です。
4.  をクリックして**開くシーンを追加**、 をクリックし、**ビルド**。

    ![ビルド設定ウィンドウ](images/AzureLabs-Lab3-43.png)

4.  ソリューションをビルドするフォルダーを選択するように促されます。 

5.  作成、*ビルド*フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。 
6.  クリックして**フォルダーの選択**をその場所にビルドを開始します。
 
    ![ビルド フォルダーを作成する](images/AzureLabs-Lab3-44.png)
    ![選択フォルダーを作成します。](images/AzureLabs-Lab3-45.png)
 
7.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了した、開く必要がありますが、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ。

ローカル コンピューターの展開。

1.  *Visual Studio*で作成されたソリューション ファイルを開き、[前のチャプター](#chapter-10--test-in-the-unity-editor)します。
2.  **ソリューション プラットフォーム**、 **x86**、**ローカル マシン**します。
3.  **ソリューション構成**選択**デバッグ**します。

    > Microsoft HoloLens にすることがあります方が簡単なこれを設定する*リモート マシン*、するは、コンピューターにテザリングされたしないようにします。 ただし、次の操作も必要があります。
    > - 把握、 **IP アドレス**内では、HoloLens の*設定 > ネットワークとインターネット > Wi-fi > 詳細オプション*;、IPv4 では、アドレスを使用する必要があります。 
    > - 確認**開発者モード**は**で**; で見つかった*設定 > 更新とセキュリティ > 開発者向け*します。

    ![アプリをデプロイします。](images/AzureLabs-Lab3-46.png)
 
4.  移動して、**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。
5.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。
6.  アプリがアクセスを承認することを求められます、起動されると、_マイク_します。 使用して、*モーションのコント ローラー*、または*音声入力*、または*キーボード*キーを押す、**はい**ボタン。 

## <a name="chapter-12--improving-your-luis-service"></a>第 12 章 –、LUIS サービスの向上

>[!IMPORTANT] 
> この章では非常に重要ですし、LUIS サービスの精度を向上させるため、バッキングストアファイルに繰り返しを複数回に付けする必要があります。 これを完了することを確認します。

LUIS によって提供される知識のレベルを向上させるためには、新しい発話をキャプチャして LUIS アプリを再トレーニングに使用する必要があります。

たとえば、LUIS"Increase"を理解して「アップサイズ」のトレーニングが可能性がありますが、アプリ「拡大」などの単語についても理解を使用することはありませんか。

アプリケーションは、何回か使用している、LUIS によって収集されると、LUIS のポータルで使用可能なすべての説明になります。

1.  その後、ポータル アプリケーションに移動[リンク](https://www.luis.ai/home)、およびログイン。
2.  MS の資格情報でログインした後は、をクリックして*アプリ名*します。
3.  をクリックして、**エンドポイント発話を確認**ページの左側にボタンをクリックします。

    ![発話を確認してください。](images/AzureLabs-Lab3-47.png)
 
4.  複合現実のアプリケーションが送信に LUIS 発話の一覧が表示されます。

    ![発話の一覧](images/AzureLabs-Lab3-48.png)
 
強調表示されたいくつかがわかります*エンティティ*します。 

強調表示されている各単語、ポインターを合わせるとすると、それぞれの発話を確認でき、エンティティが認識されている正しく、エンティティが正しくないが、エンティティが欠落を判断することができます。

上記の例では、それが見つかったこと「スピア型」という単語が強調表示されて、ターゲットとしてそのため、ポインターを合わせると、マウスを使用して単語をクリックして実行されると、誤りを修正するために必要な**ラベルの削除**します。

![発話の確認](images/AzureLabs-Lab3-49.png)
![ラベル イメージの削除](images/AzureLabs-Lab3-50.png)
 
5.  言葉を完全に間違っている場合は、削除するを使用して、**削除**画面の右側にあるボタンをクリックします。

    ![間違った発話を削除します。](images/AzureLabs-Lab3-51.png)

6.  使用して内容を理解を検証するには、LUIS が発話を正しく解釈がある場合、または、**配置目的に追加**ボタンをクリックします。

    ![配置済みのインテントに追加します。](images/AzureLabs-Lab3-52.png)

7.  表示されているすべての発話を並べ替えた後以上が使用可能なかどうかに表示するページを再読み込みをしてください。
8.  アプリケーションについての理解を向上させるために可能な回数だけこのプロセスを繰り返す非常に重要ですが。 

**楽しんでください！**

## <a name="your-finished-luis-integrated-application"></a>完成した LUIS 統合アプリケーション

これで、Azure Language Understanding Intelligence Service、ユーザーの質問を理解して、その情報を活用する mixed reality アプリを構築します。

![ラボの結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

このアプリケーションの使用中にいる場合、Floor オブジェクトを見つめます、色を変更するように要求して、その処理を行いますがわかります。 床面の色を変更することから、アプリケーションを停止する方法を操作することができますか。

### <a name="exercise-2"></a>手順 2

シーン内のオブジェクトの機能の追加の LUIS とアプリの機能の拡張をお試しください。たとえば、ヒット ポイントは、どのようなユーザーによって言うし、現在のシーン オブジェクトと共にそれらのオブジェクトを使用して、既存のコマンドを使用できる視線の先に新しいオブジェクトを作成します。 
