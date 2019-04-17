---
title: 貢献する手順
description: Windows Mixed Reality ドキュメントに投稿する方法。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604651"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Windows Mixed Reality 開発者向けドキュメントに貢献します。

ようこそ、 [Windows Mixed Reality 開発者向けドキュメントのパブリック リポジトリ](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! アーティクルを作成またはこのリポジトリで編集する**パブリックに表示されます。** 

Windows Mixed Reality ドキュメントは、GitHub flavored Markdown (Markdig 機能) を使用して、docs.microsoft.com プラットフォームではようになりました。 表示される書式設定と図案化されたページにこのリポジトリを編集するコンテンツを取得になっている基本的に、 https://docs.microsoft.com/windows/mixed-realityします。 

このページの基本的な手順と、投稿するためのガイドラインについて説明し、Markdown の基本にリンクします。 あなたの投稿をありがとうございます。

## <a name="before-you-start"></a>開始前の作業

1 つをいない場合は、する必要があります[GitHub アカウントを作成する](https://github.com/join)します。

>[!NOTE]
>Microsoft 従業員の場合は、GitHub アカウントに、Microsoft エイリアスをリンクを[Microsoft のオープン ソース ポータル](https://repos.opensource.microsoft.com/)します。 結合、 **"Microsoft"** と **"MicrosoftDocs"** 組織)。

GitHub アカウントを設定するときにこれらのセキュリティ予防措置も推奨します。
- 作成、 [、Github アカウントに強力なパスワード](https://github.com/settings/admin)します。
- 有効にする[2 要素認証](https://github.com/settings/two_factor_authentication/configure)します。
- 保存、[復旧コード](https://github.com/settings/auth/recovery-codes)安全な場所。
- 更新プログラム、[パブリック プロファイル設定](https://github.com/settings/profile)します。
   - 自分の名前を設定し、設定を検討してください、*パブリック電子メール*に*自分のメール アドレスを表示しない*します。
   - として投稿する docs ページのサムネイルが表示されます、プロファイル画像をアップロードすることをお勧めします。
- コマンド ライン ワークフローを使用する場合は、設定を検討してください。 [Windows 用の Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)の投稿を行うたびに、パスワードを入力する必要がないようにします。

これらの手順を実行することは、発行のシステムが GitHub に関連付けられているし、する作成者または共同作成者に、GitHub のエイリアスを使用して各アーティクルのいずれかとして表示されます、重要です。

## <a name="editing-an-existing-article"></a>既存のアーティクルの編集

次のワークフローを使用するための更新して*既存のアーティクル*web ブラウザーで GitHub 経由で。

1. "混合-実際には、docs"フォルダーで編集する記事に移動します。
2. 右上にある編集ボタン (鉛筆のアイコン) を選択します。 破棄可能な分岐 'マスター' ブランチをオフにこれは自動的に分岐します。

   ![記事を編集します。](images/editpage.png)
3. 記事の内容を編集 (を参照してください[「Markdown の基本」](#markdown-basics)以下のガイダンスについては)。
4. 各記事の上部にある関連するメタデータを更新します。
   * タイトル:これは、記事が表示されていると、[ブラウザー] タブに表示されるページのタイトルです。 SEO およびインデックス作成に使用される、のでしない限り、タイトルを変更することはできません (ただし、これは、ドキュメントが公開する前に、重要度の低い) に必要です。
   * description:記事の内容の簡単な説明を記述します。 SEO と検出を容易にします。
   * 作成者:ページのプライマリ所有者の場合は、ここで、GitHub のエイリアスを追加します。
   * ms.author:ページのプライマリ所有者の場合は、追加のエイリアスは、ここ、マイクロソフト (する必要はありません@microsoft.com、エイリアスだけです)。
   * ms.date:詳細については、書式設定、文法のように修正プログラムではなく、ページに、主要なコンテンツを追加するかもスペル チェックは、日付を更新します。
   * キーワード:キーワードは SEO (検索エンジンの最適化) を支援します。 キーワードを追加して、コンマとスペースで区切られた記事 (ただし、リストの最後のキーワードの後に句読点); に固有の他の場所で管理されているように、すべてのアーティクルに適用されるグローバルのキーワードを追加する必要はありません。 
5. 記事の編集が完了したら、下にスクロールし、をクリックして、**ファイルの変更提案**ボタンをクリックします。
6. 次のページで次のようにクリックします**プル要求の作成**'マスター。' に、自動的に作成されたブランチをマージするには。
7. 次の資料を編集するには、上記の手順を繰り返します。

## <a name="creating-a-new-article"></a>新しいアーティクルの作成

次のワークフローを使用して、*記事を新規作成*web ブラウザーで GitHub を使用して、ドキュメント リポジトリで。

1. MicrosoftDocs/複合現実 'マスター' ブランチをフォークを作成 (を使用して、**フォーク**右上のボタン)。

   ![Master ブランチをフォークします。](images/forkbranch.png)
2. "混合-実際には、docs"フォルダーで、をクリックして、**新しいファイルの作成**右上のボタンをクリックします。
3. ページ名、記事の作成 (スペースの代わりにハイフンを使用して、および句読点やアポストロフィを使用しない) と".md"を追加

   ![新しいページの名前を付けます。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >"混合-実際には、docs"フォルダー内から新しいアーティクルを作成することを確認します。 これをチェックして確認できます"/mixed reality docs/"で新しいファイル名の行。

4. 新しいページの上部にある次のメタデータのブロックを追加します。

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. 手順に従って、関連するメタデータ フィールドに入力、[前のセクション](#editing-an-existing-article)します。
6. 書き込みの記事を使用してコンテンツ[Markdown の基本](#markdown-basics)します。
7. 追加、`## See also`と他の関連記事へのリンク、記事の下部のセクション。
8. 完了したら、クリックして**コミットの新しいファイル**します。
9. クリックして**新しいプル要求**MicrosoftDocs/複合現実 'master' にフォークの 'マスター' ブランチをマージし、(矢印が正しい方法を指していることを確認してください)。

   ![MicrosoftDocs/複合現実に自分のフォークからプル要求を作成する.](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown の基本

次のリソースを使用すると、Markdown 言語を使用してドキュメントを編集する方法を説明できます。

- [Markdown の基本](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [概要でのマークダウン リファレンスのポスター](images/MarkdownPoster.pdf)
- [Docs.microsoft.com の Markdown を記述するための他のリソース](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>テーブルの追加

、Docs.microsoft.com のスタイルのテーブルの方法により必要がある境界線またはカスタム スタイルは、場合でも、インライン CSS を再試行してください。 短時間、作業に表示されますが、最終的に、プラットフォームは、テーブルのスタイルを削除します。 事前に計画し、単純なテーブルようにします。 [Markdown のテーブルを容易にするサイトを次に示します](http://www.tablesgenerator.com/markdown_tables)します。

[Visual Studio Code 用 Docs Markdown Extension](https://docs.microsoft.com/teamblog/docs-extension)によりを使用する場合に簡単に生成をどのようにテーブルも[Visual Studio Code (下記参照)](#using-visual-studio-code)ドキュメントを編集します。

### <a name="adding-images"></a>イメージを追加します。

リポジトリで"混在-実際には、docs/images"フォルダーに、イメージをアップロードし、それらを情報の記事で適切に参照する必要があります。 イメージに表示が自動的にフルサイズ、つまり、この記事の幅全体を入力します、イメージのサイズが大きい場合。 そのため、事前にアップロードする前に、イメージ サイズ変更をお勧めします。 推奨される幅は、高密度のスクリーン ショットまたはスクリーン ショットを分数でそれぞれある場合、アップまたはスケール ダウンを調整する必要がありますが、600 ~ 700 のピクセルの場合は。

>[!IMPORTANT]
>イメージは、マージする前に、フォークしたレポジトリにのみアップロードできます。 そのため、アーティクルにイメージを追加する場合は、する必要があります[Visual Studio Code を使用して、](#using-visual-studio-code)最初、フォークの"images"フォルダーにイメージを追加するか、web ブラウザーでは、次を実行したかどうかを確認します。
>
>1. MicrosoftDocs/複合現実のリポジトリをフォークします。
>2. フォーク内の記事を編集します。
>3. フォークに"混在-実際には、docs/images"フォルダーに、記事を参照しているイメージをアップロードします。
>4. 作成、**プル要求**MicrosoftDocs/複合現実 'マスター' ブランチに独自のフォークをマージします。
>
>独自のフォークしたレポジトリを設定する方法については、手順に従います[新しいアーティクルを作成する](#creating-a-new-article)します。

## <a name="previewing-your-work"></a>作業内容をプレビューします。

クリックすることができます、web ブラウザーから GitHub で編集している間、**プレビュー**をコミットする前に作業内容をプレビューするページの上部付近のタブ。 

>[!NOTE]
>Review.docs.microsoft.com で変更のプレビューのみが利用できる Microsoft の従業員

Microsoft の従業員: お客様の投稿物は、'マスター' ブランチにマージされましたが後のドキュメントの外観に公表前に参照してくださいできます https://review.docs.microsoft.com/windows/mixed-reality?branch=master(左側にある目次を使用して、記事を検索)。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>デスクトップ クライアントで編集すると、ブラウザーでの編集

小さな変更を加えるの最も簡単な方法は、ブラウザーでの編集、ただし、いくつかの短所があります。

- スペル チェックを得られません。
- すべてスマート リンク (記事のファイル名を手動で入力する必要がある) の他の記事には得られません。
- アップロードして、イメージを参照する面倒な作業になります。

これらの問題をしない扱うはではなく場合、は、デスクトップのようにクライアントを使用することができます[Visual Studio Code](https://code.visualstudio.com/)がいくつか[役立つ拡張機能](#useful-extensions)ドキュメントに投稿します。

## <a name="using-visual-studio-code"></a>Visual Studio Code の使用

上の理由から、表示されている[上](#editing-in-the-browser-vs-editing-with-a-desktop-client)、デスクトップ クライアントを使用して、web ブラウザーではなくドキュメントを編集することもできます。 使用することをお勧めします。 [Visual Studio Code](https://code.visualstudio.com/)します。

### <a name="setup"></a>セットアップ

このリポジトリを使用する Visual Studio Code を構成するこれらの手順に従います。

1. Web ブラウザー。
    1. インストール[PC の Git](https://git-scm.com/downloads)します。
    2. インストール[Visual Studio Code](https://code.visualstudio.com/)します。
    3. [フォーク MicrosoftDocs/複合現実](#creating-a-new-article)まだ行っていない場合。
    4. 独自のフォークでクリックして**複製またはダウンロード**URL をコピーします。
2. Visual Studio Code で、フォークのローカル クローンを作成します。
    1. **ビュー**メニューの **コマンド パレット**します。
    2. 型"Git:Clone"
    3. コピーした URL を貼り付けます。
    4. PC のクローンを保存する場所を選択します。
    5. をクリックして**オープン リポジトリ**ポップアップします。

### <a name="editing-documentation"></a>ドキュメントの編集

Visual Studio Code のドキュメントを変更するのにには、次のワークフローを使用します。

>[!NOTE]
>すべてのガイダンス[編集](#editing-an-existing-article)と[作成](#creating-a-new-article)記事、および[Markdown を編集の基本](#markdown-basics)、上からも、Visual Studio Code を使用するときに適用されます。

1. 複製、フォークは、公式のリポジトリの最新の状態を確認します。
   1. Web ブラウザーで独自のフォークに MicrosoftDocs/複合現実 'master' 内の他の共同作成者からの最近の変更を同期するプル要求を作成します (矢印が適切な方法を指していることを確認してください)。
      
      ![独自のフォークに MicrosoftDocs/複合現実から変更の同期](images/sync_repos.PNG)
   2. Visual Studio Code で、新しく更新されたフォークをローカルの複製を同期する同期 ボタンをクリックします。
      
      ![[同期] ボタンをクリックします。](images/sync_clone.png)
2. 作成するか、Visual Studio Code を使用して、複製されたリポジトリ内のアーティクルを編集します。
   1. (追加イメージ"の images"フォルダーに必要な場合)、1 つまたは複数の記事を編集します。
   2. **保存**変更**エクスプ ローラー**します。
      
      ![エクスプ ローラーで [すべて保存] を選択します。](images/explorer_save.png)
   3. **すべてをコミット**変更**ソース管理**(書き込みコミット メッセージが表示されたら)。
      
      ![「すべてコミット」でソース管理を選択します。](images/source_control_commit.png)
   4. をクリックして、**同期**同期の配信元 (GitHub で独自のフォーク) を変更するボタンをクリックします。
      
      ![[同期] ボタンをクリックします。](images/sync_back.png)
3. Web ブラウザーで新しいフォーク MicrosoftDocs/複合現実 'master' に変更を同期するプル要求の作成 (矢印が正しい方法を指していることを確認してください)。

   ![MicrosoftDocs/複合現実に自分のフォークからプル要求を作成する.](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用な拡張機能

次の Visual Studio Code 拡張機能は、ドキュメントを編集する際に非常に便利です。

- [Visual Studio Code 用 docs Markdown Extension](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -使用**Alt + M** docs の作成などのオプションのメニューを表示します。
   - アップロードしたイメージ検索と参照。
   - テーブルを一覧表示などの書式設定となどの docs 固有の注意を追加`>[!NOTE]`します。
   - 検索し、内部リンクやブックマーク (ページ内の特定セクションへのリンク) を参照します。
   - 書式設定エラーが強調表示されます (詳細については、エラーの上にマウスを移動) します。
- [スペル チェックをコード](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-スペル ミスの単語が付いて; を変更したり、ディクショナリに保存してスペル ミスの単語を右クリックします。
