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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="b6e29-103">Windows Mixed Reality 開発者向けドキュメントに貢献します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="b6e29-104">ようこそ、 [Windows Mixed Reality 開発者向けドキュメントのパブリック リポジトリ](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="b6e29-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="b6e29-105">アーティクルを作成またはこのリポジトリで編集する**パブリックに表示されます。**</span><span class="sxs-lookup"><span data-stu-id="b6e29-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="b6e29-106">Windows Mixed Reality ドキュメントは、GitHub flavored Markdown (Markdig 機能) を使用して、docs.microsoft.com プラットフォームではようになりました。</span><span class="sxs-lookup"><span data-stu-id="b6e29-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="b6e29-107">表示される書式設定と図案化されたページにこのリポジトリを編集するコンテンツを取得になっている基本的に、 https://docs.microsoft.com/windows/mixed-realityします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="b6e29-108">このページの基本的な手順と、投稿するためのガイドラインについて説明し、Markdown の基本にリンクします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="b6e29-109">あなたの投稿をありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b6e29-110">開始前の作業</span><span class="sxs-lookup"><span data-stu-id="b6e29-110">Before you start</span></span>

<span data-ttu-id="b6e29-111">1 つをいない場合は、する必要があります[GitHub アカウントを作成する](https://github.com/join)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="b6e29-112">Microsoft 従業員の場合は、GitHub アカウントに、Microsoft エイリアスをリンクを[Microsoft のオープン ソース ポータル](https://repos.opensource.microsoft.com/)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="b6e29-113">結合、 **"Microsoft"** と **"MicrosoftDocs"** 組織)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="b6e29-114">GitHub アカウントを設定するときにこれらのセキュリティ予防措置も推奨します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="b6e29-115">作成、 [、Github アカウントに強力なパスワード](https://github.com/settings/admin)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="b6e29-116">有効にする[2 要素認証](https://github.com/settings/two_factor_authentication/configure)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="b6e29-117">保存、[復旧コード](https://github.com/settings/auth/recovery-codes)安全な場所。</span><span class="sxs-lookup"><span data-stu-id="b6e29-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="b6e29-118">更新プログラム、[パブリック プロファイル設定](https://github.com/settings/profile)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="b6e29-119">自分の名前を設定し、設定を検討してください、*パブリック電子メール*に*自分のメール アドレスを表示しない*します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="b6e29-120">として投稿する docs ページのサムネイルが表示されます、プロファイル画像をアップロードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="b6e29-121">コマンド ライン ワークフローを使用する場合は、設定を検討してください。 [Windows 用の Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)の投稿を行うたびに、パスワードを入力する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="b6e29-122">これらの手順を実行することは、発行のシステムが GitHub に関連付けられているし、する作成者または共同作成者に、GitHub のエイリアスを使用して各アーティクルのいずれかとして表示されます、重要です。</span><span class="sxs-lookup"><span data-stu-id="b6e29-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="b6e29-123">既存のアーティクルの編集</span><span class="sxs-lookup"><span data-stu-id="b6e29-123">Editing an existing article</span></span>

<span data-ttu-id="b6e29-124">次のワークフローを使用するための更新して*既存のアーティクル*web ブラウザーで GitHub 経由で。</span><span class="sxs-lookup"><span data-stu-id="b6e29-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="b6e29-125">"混合-実際には、docs"フォルダーで編集する記事に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="b6e29-126">右上にある編集ボタン (鉛筆のアイコン) を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="b6e29-127">破棄可能な分岐 'マスター' ブランチをオフにこれは自動的に分岐します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![記事を編集します。](images/editpage.png)
3. <span data-ttu-id="b6e29-129">記事の内容を編集 (を参照してください[「Markdown の基本」](#markdown-basics)以下のガイダンスについては)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="b6e29-130">各記事の上部にある関連するメタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="b6e29-131">タイトル:これは、記事が表示されていると、[ブラウザー] タブに表示されるページのタイトルです。</span><span class="sxs-lookup"><span data-stu-id="b6e29-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="b6e29-132">SEO およびインデックス作成に使用される、のでしない限り、タイトルを変更することはできません (ただし、これは、ドキュメントが公開する前に、重要度の低い) に必要です。</span><span class="sxs-lookup"><span data-stu-id="b6e29-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="b6e29-133">description:記事の内容の簡単な説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="b6e29-134">SEO と検出を容易にします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="b6e29-135">作成者:ページのプライマリ所有者の場合は、ここで、GitHub のエイリアスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="b6e29-136">ms.author:ページのプライマリ所有者の場合は、追加のエイリアスは、ここ、マイクロソフト (する必要はありません@microsoft.com、エイリアスだけです)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="b6e29-137">ms.date:詳細については、書式設定、文法のように修正プログラムではなく、ページに、主要なコンテンツを追加するかもスペル チェックは、日付を更新します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="b6e29-138">キーワード:キーワードは SEO (検索エンジンの最適化) を支援します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="b6e29-139">キーワードを追加して、コンマとスペースで区切られた記事 (ただし、リストの最後のキーワードの後に句読点); に固有の他の場所で管理されているように、すべてのアーティクルに適用されるグローバルのキーワードを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b6e29-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="b6e29-140">記事の編集が完了したら、下にスクロールし、をクリックして、**ファイルの変更提案**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="b6e29-141">次のページで次のようにクリックします**プル要求の作成**'マスター。' に、自動的に作成されたブランチをマージするには。</span><span class="sxs-lookup"><span data-stu-id="b6e29-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="b6e29-142">次の資料を編集するには、上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="b6e29-143">新しいアーティクルの作成</span><span class="sxs-lookup"><span data-stu-id="b6e29-143">Creating a new article</span></span>

<span data-ttu-id="b6e29-144">次のワークフローを使用して、*記事を新規作成*web ブラウザーで GitHub を使用して、ドキュメント リポジトリで。</span><span class="sxs-lookup"><span data-stu-id="b6e29-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="b6e29-145">MicrosoftDocs/複合現実 'マスター' ブランチをフォークを作成 (を使用して、**フォーク**右上のボタン)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Master ブランチをフォークします。](images/forkbranch.png)
2. <span data-ttu-id="b6e29-147">"混合-実際には、docs"フォルダーで、をクリックして、**新しいファイルの作成**右上のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="b6e29-148">ページ名、記事の作成 (スペースの代わりにハイフンを使用して、および句読点やアポストロフィを使用しない) と".md"を追加</span><span class="sxs-lookup"><span data-stu-id="b6e29-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![新しいページの名前を付けます。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="b6e29-150">"混合-実際には、docs"フォルダー内から新しいアーティクルを作成することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="b6e29-151">これをチェックして確認できます"/mixed reality docs/"で新しいファイル名の行。</span><span class="sxs-lookup"><span data-stu-id="b6e29-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="b6e29-152">新しいページの上部にある次のメタデータのブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="b6e29-153">手順に従って、関連するメタデータ フィールドに入力、[前のセクション](#editing-an-existing-article)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="b6e29-154">書き込みの記事を使用してコンテンツ[Markdown の基本](#markdown-basics)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="b6e29-155">追加、`## See also`と他の関連記事へのリンク、記事の下部のセクション。</span><span class="sxs-lookup"><span data-stu-id="b6e29-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="b6e29-156">完了したら、クリックして**コミットの新しいファイル**します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="b6e29-157">クリックして**新しいプル要求**MicrosoftDocs/複合現実 'master' にフォークの 'マスター' ブランチをマージし、(矢印が正しい方法を指していることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![MicrosoftDocs/複合現実に自分のフォークからプル要求を作成する.](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="b6e29-159">Markdown の基本</span><span class="sxs-lookup"><span data-stu-id="b6e29-159">Markdown basics</span></span>

<span data-ttu-id="b6e29-160">次のリソースを使用すると、Markdown 言語を使用してドキュメントを編集する方法を説明できます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="b6e29-161">Markdown の基本</span><span class="sxs-lookup"><span data-stu-id="b6e29-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="b6e29-162">概要でのマークダウン リファレンスのポスター</span><span class="sxs-lookup"><span data-stu-id="b6e29-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="b6e29-163">Docs.microsoft.com の Markdown を記述するための他のリソース</span><span class="sxs-lookup"><span data-stu-id="b6e29-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="b6e29-164">テーブルの追加</span><span class="sxs-lookup"><span data-stu-id="b6e29-164">Adding tables</span></span>

<span data-ttu-id="b6e29-165">、Docs.microsoft.com のスタイルのテーブルの方法により必要がある境界線またはカスタム スタイルは、場合でも、インライン CSS を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="b6e29-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="b6e29-166">短時間、作業に表示されますが、最終的に、プラットフォームは、テーブルのスタイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="b6e29-167">事前に計画し、単純なテーブルようにします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="b6e29-168">[Markdown のテーブルを容易にするサイトを次に示します](http://www.tablesgenerator.com/markdown_tables)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="b6e29-169">[Visual Studio Code 用 Docs Markdown Extension](https://docs.microsoft.com/teamblog/docs-extension)によりを使用する場合に簡単に生成をどのようにテーブルも[Visual Studio Code (下記参照)](#using-visual-studio-code)ドキュメントを編集します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="b6e29-170">イメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-170">Adding images</span></span>

<span data-ttu-id="b6e29-171">リポジトリで"混在-実際には、docs/images"フォルダーに、イメージをアップロードし、それらを情報の記事で適切に参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6e29-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="b6e29-172">イメージに表示が自動的にフルサイズ、つまり、この記事の幅全体を入力します、イメージのサイズが大きい場合。</span><span class="sxs-lookup"><span data-stu-id="b6e29-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="b6e29-173">そのため、事前にアップロードする前に、イメージ サイズ変更をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="b6e29-174">推奨される幅は、高密度のスクリーン ショットまたはスクリーン ショットを分数でそれぞれある場合、アップまたはスケール ダウンを調整する必要がありますが、600 ~ 700 のピクセルの場合は。</span><span class="sxs-lookup"><span data-stu-id="b6e29-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b6e29-175">イメージは、マージする前に、フォークしたレポジトリにのみアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="b6e29-176">そのため、アーティクルにイメージを追加する場合は、する必要があります[Visual Studio Code を使用して、](#using-visual-studio-code)最初、フォークの"images"フォルダーにイメージを追加するか、web ブラウザーでは、次を実行したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="b6e29-177">MicrosoftDocs/複合現実のリポジトリをフォークします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="b6e29-178">フォーク内の記事を編集します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="b6e29-179">フォークに"混在-実際には、docs/images"フォルダーに、記事を参照しているイメージをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="b6e29-180">作成、**プル要求**MicrosoftDocs/複合現実 'マスター' ブランチに独自のフォークをマージします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="b6e29-181">独自のフォークしたレポジトリを設定する方法については、手順に従います[新しいアーティクルを作成する](#creating-a-new-article)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="b6e29-182">作業内容をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-182">Previewing your work</span></span>

<span data-ttu-id="b6e29-183">クリックすることができます、web ブラウザーから GitHub で編集している間、**プレビュー**をコミットする前に作業内容をプレビューするページの上部付近のタブ。</span><span class="sxs-lookup"><span data-stu-id="b6e29-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="b6e29-184">Review.docs.microsoft.com で変更のプレビューのみが利用できる Microsoft の従業員</span><span class="sxs-lookup"><span data-stu-id="b6e29-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="b6e29-185">Microsoft の従業員: お客様の投稿物は、'マスター' ブランチにマージされましたが後のドキュメントの外観に公表前に参照してくださいできます https://review.docs.microsoft.com/windows/mixed-reality?branch=master(左側にある目次を使用して、記事を検索)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="b6e29-186">デスクトップ クライアントで編集すると、ブラウザーでの編集</span><span class="sxs-lookup"><span data-stu-id="b6e29-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="b6e29-187">小さな変更を加えるの最も簡単な方法は、ブラウザーでの編集、ただし、いくつかの短所があります。</span><span class="sxs-lookup"><span data-stu-id="b6e29-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="b6e29-188">スペル チェックを得られません。</span><span class="sxs-lookup"><span data-stu-id="b6e29-188">You don't get spell-check.</span></span>
- <span data-ttu-id="b6e29-189">すべてスマート リンク (記事のファイル名を手動で入力する必要がある) の他の記事には得られません。</span><span class="sxs-lookup"><span data-stu-id="b6e29-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="b6e29-190">アップロードして、イメージを参照する面倒な作業になります。</span><span class="sxs-lookup"><span data-stu-id="b6e29-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="b6e29-191">これらの問題をしない扱うはではなく場合、は、デスクトップのようにクライアントを使用することができます[Visual Studio Code](https://code.visualstudio.com/)がいくつか[役立つ拡張機能](#useful-extensions)ドキュメントに投稿します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="b6e29-192">Visual Studio Code の使用</span><span class="sxs-lookup"><span data-stu-id="b6e29-192">Using Visual Studio Code</span></span>

<span data-ttu-id="b6e29-193">上の理由から、表示されている[上](#editing-in-the-browser-vs-editing-with-a-desktop-client)、デスクトップ クライアントを使用して、web ブラウザーではなくドキュメントを編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="b6e29-194">使用することをお勧めします。 [Visual Studio Code](https://code.visualstudio.com/)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="b6e29-195">セットアップ</span><span class="sxs-lookup"><span data-stu-id="b6e29-195">Setup</span></span>

<span data-ttu-id="b6e29-196">このリポジトリを使用する Visual Studio Code を構成するこれらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b6e29-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="b6e29-197">Web ブラウザー。</span><span class="sxs-lookup"><span data-stu-id="b6e29-197">In a web browser:</span></span>
    1. <span data-ttu-id="b6e29-198">インストール[PC の Git](https://git-scm.com/downloads)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="b6e29-199">インストール[Visual Studio Code](https://code.visualstudio.com/)します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="b6e29-200">[フォーク MicrosoftDocs/複合現実](#creating-a-new-article)まだ行っていない場合。</span><span class="sxs-lookup"><span data-stu-id="b6e29-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="b6e29-201">独自のフォークでクリックして**複製またはダウンロード**URL をコピーします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="b6e29-202">Visual Studio Code で、フォークのローカル クローンを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="b6e29-203">**ビュー**メニューの **コマンド パレット**します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="b6e29-204">型"Git:Clone"</span><span class="sxs-lookup"><span data-stu-id="b6e29-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="b6e29-205">コピーした URL を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="b6e29-206">PC のクローンを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="b6e29-207">をクリックして**オープン リポジトリ**ポップアップします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="b6e29-208">ドキュメントの編集</span><span class="sxs-lookup"><span data-stu-id="b6e29-208">Editing documentation</span></span>

<span data-ttu-id="b6e29-209">Visual Studio Code のドキュメントを変更するのにには、次のワークフローを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="b6e29-210">すべてのガイダンス[編集](#editing-an-existing-article)と[作成](#creating-a-new-article)記事、および[Markdown を編集の基本](#markdown-basics)、上からも、Visual Studio Code を使用するときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b6e29-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="b6e29-211">複製、フォークは、公式のリポジトリの最新の状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="b6e29-212">Web ブラウザーで独自のフォークに MicrosoftDocs/複合現実 'master' 内の他の共同作成者からの最近の変更を同期するプル要求を作成します (矢印が適切な方法を指していることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![独自のフォークに MicrosoftDocs/複合現実から変更の同期](images/sync_repos.PNG)
   2. <span data-ttu-id="b6e29-214">Visual Studio Code で、新しく更新されたフォークをローカルの複製を同期する同期 ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![[同期] ボタンをクリックします。](images/sync_clone.png)
2. <span data-ttu-id="b6e29-216">作成するか、Visual Studio Code を使用して、複製されたリポジトリ内のアーティクルを編集します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="b6e29-217">(追加イメージ"の images"フォルダーに必要な場合)、1 つまたは複数の記事を編集します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="b6e29-218">**保存**変更**エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-218">**Save** changes in **Explorer**.</span></span>
      
      ![エクスプ ローラーで [すべて保存] を選択します。](images/explorer_save.png)
   3. <span data-ttu-id="b6e29-220">**すべてをコミット**変更**ソース管理**(書き込みコミット メッセージが表示されたら)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![「すべてコミット」でソース管理を選択します。](images/source_control_commit.png)
   4. <span data-ttu-id="b6e29-222">をクリックして、**同期**同期の配信元 (GitHub で独自のフォーク) を変更するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![[同期] ボタンをクリックします。](images/sync_back.png)
3. <span data-ttu-id="b6e29-224">Web ブラウザーで新しいフォーク MicrosoftDocs/複合現実 'master' に変更を同期するプル要求の作成 (矢印が正しい方法を指していることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="b6e29-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![MicrosoftDocs/複合現実に自分のフォークからプル要求を作成する.](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="b6e29-226">有用な拡張機能</span><span class="sxs-lookup"><span data-stu-id="b6e29-226">Useful extensions</span></span>

<span data-ttu-id="b6e29-227">次の Visual Studio Code 拡張機能は、ドキュメントを編集する際に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="b6e29-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="b6e29-228">[Visual Studio Code 用 docs Markdown Extension](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -使用**Alt + M** docs の作成などのオプションのメニューを表示します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="b6e29-229">アップロードしたイメージ検索と参照。</span><span class="sxs-lookup"><span data-stu-id="b6e29-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="b6e29-230">テーブルを一覧表示などの書式設定となどの docs 固有の注意を追加`>[!NOTE]`します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="b6e29-231">検索し、内部リンクやブックマーク (ページ内の特定セクションへのリンク) を参照します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="b6e29-232">書式設定エラーが強調表示されます (詳細については、エラーの上にマウスを移動) します。</span><span class="sxs-lookup"><span data-stu-id="b6e29-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="b6e29-233">[スペル チェックをコード](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-スペル ミスの単語が付いて; を変更したり、ディクショナリに保存してスペル ミスの単語を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="b6e29-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
