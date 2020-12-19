---
title: 関与する指示
description: GitHub-flavored Markdown を使用して、docs.microsoft.com プラットフォームで Mixed Reality 開発者ドキュメントに投稿する方法について説明します。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 0a71072a27befc4295b82e1235cbc75655743056
ms.sourcegitcommit: 0b406ccbc7ce619e42809ba8dfdc47d83f4917ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97691320"
---
# <a name="contributing-to-mixed-reality-developer-documentation"></a><span data-ttu-id="9b0a1-103">Mixed Reality 開発者向けドキュメントへの貢献</span><span class="sxs-lookup"><span data-stu-id="9b0a1-103">Contributing to Mixed Reality developer documentation</span></span>

<span data-ttu-id="9b0a1-104">[Mixed Reality 開発者向けドキュメントのパブリックリポジトリ](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)へようこそ。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-104">Welcome to the [public repo for Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="9b0a1-105">このリポジトリで作成または編集した記事 **は、パブリックに表示されます。**</span><span class="sxs-lookup"><span data-stu-id="9b0a1-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="9b0a1-106">Mixed Reality ドキュメントは現在、docs.microsoft.com プラットフォームにあります。これは、flavored Markdown を Markdig 特徴と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-106">The Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown with Markdig features.</span></span> <span data-ttu-id="9b0a1-107">このリポジトリで編集するコンテンツは、に表示される定型ページに書式設定され https://docs.microsoft.com/windows/mixed-reality ます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-107">The content you edit in this repo gets formatted into stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> <span data-ttu-id="9b0a1-108">HoloLens または VR のドキュメントに投稿する場合は、それぞれの [hololens](https://github.com/MicrosoftDocs/Hololens) および [vr](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) リポジトリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-108">If you want to contribute to HoloLens or VR enthusiast documentation, visit their respective [HoloLens](https://github.com/MicrosoftDocs/Hololens) and [VR](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) repositories.</span></span>

<span data-ttu-id="9b0a1-109">このページでは、Markdown の基本に寄与するための基本的な手順とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-109">This page covers the basic steps and guidelines for contributing and links to Markdown basics.</span></span> <span data-ttu-id="9b0a1-110">投稿いただき、ありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-110">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9b0a1-111">開始する前に</span><span class="sxs-lookup"><span data-stu-id="9b0a1-111">Before you start</span></span>

<span data-ttu-id="9b0a1-112">まだお持ちでない場合は、 [GitHub アカウントを作成](https://github.com/join)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-112">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="9b0a1-113">Microsoft の従業員の場合は、microsoft [オープンソースポータル](https://repos.opensource.microsoft.com/)で GitHub アカウントを microsoft エイリアスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-113">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="9b0a1-114">**"Microsoft"** と "microsoft **docs"** の組織に参加してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-114">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="9b0a1-115">GitHub アカウントを設定するときは、次のセキュリティに関する注意事項もお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-115">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="9b0a1-116">[Github アカウントの強力なパスワード](https://github.com/settings/admin)を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-116">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="9b0a1-117">[2 要素認証](https://github.com/settings/two_factor_authentication/configure)を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-117">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="9b0a1-118">[回復コード](https://github.com/settings/auth/recovery-codes)を安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-118">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="9b0a1-119">[パブリックプロファイルの設定](https://github.com/settings/profile)を更新します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-119">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="9b0a1-120">自分の名前を設定し、電子メールアドレスを *表示しない* ように *パブリック電子メール* を設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-120">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="9b0a1-121">プロフィール画像をアップロードすることをお勧めします。これは、投稿するドキュメントページにサムネイルが表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-121">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="9b0a1-122">コマンドラインを使用する場合は、 [Windows 用の Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)を設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-122">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="9b0a1-123">これにより、投稿を行うたびにパスワードを入力する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-123">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="9b0a1-124">発行システムは GitHub に関連付けられているため、これらの手順は重要です。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-124">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="9b0a1-125">GitHub エイリアスを使用して、各記事の作成者または共同作成者として一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-125">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="9b0a1-126">既存の記事の編集</span><span class="sxs-lookup"><span data-stu-id="9b0a1-126">Editing an existing article</span></span>

<span data-ttu-id="9b0a1-127">次のワークフローを使用して、web ブラウザーで GitHub 経由で *既存の記事* の更新を行います。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-127">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="9b0a1-128">"Mixed-reality" フォルダーで、編集する記事に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-128">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="9b0a1-129">右上の [編集] ボタン (鉛筆アイコン) を選択すると、"マスター" 分岐から破棄可能な分岐が自動的にフォークされます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-129">Select the edit button (pencil icon) in the top right, which will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![記事を編集します。](images/editpage.png)
3. <span data-ttu-id="9b0a1-131">[「Markdown の基礎」](#markdown-basics)に従って、記事の内容を編集します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-131">Edit the content of the article according to the ["Markdown basics"](#markdown-basics).</span></span>
4. <span data-ttu-id="9b0a1-132">各記事の上部にあるメタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-132">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="9b0a1-133">**title**: 記事が表示されているときに [ブラウザー] タブに表示されるページタイトル。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-133">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="9b0a1-134">ページタイトルは、SEO とインデックス作成に使用されるため、必要な場合以外はタイトルを変更しないでください (ただし、ドキュメントが公開される前には重要度が低くなります)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-134">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="9b0a1-135">**description**: 記事のコンテンツに関する簡単な説明を記述します。これにより、SEO と検出が向上します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-135">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="9b0a1-136">**author**: ページのプライマリ所有者である場合は、ここに GitHub エイリアスを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-136">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="9b0a1-137">**ms. author**: ページのプライマリ所有者である場合は、ここに Microsoft エイリアスを追加します (必要なのはエイリアスではありません @microsoft.com )。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-137">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="9b0a1-138">**ms. date**: ページに主要なコンテンツを追加する場合は日付を更新します。ただし、明確、書式設定、文法、スペルなどの修正には使用しません。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-138">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="9b0a1-139">**キーワード**: キーワードは、SEO (検索エンジンの最適化) に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-139">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="9b0a1-140">コンマとスペースで区切られたキーワードを追加します。これは、記事に固有のものですが、リスト内の最後のキーワードの後には句読点がありません。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-140">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="9b0a1-141">すべての記事に適用するグローバルキーワードを追加する必要はありません。他の場所で管理されているためです。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-141">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="9b0a1-142">記事の編集が完了したら、下にスクロールして [ **ファイル変更の提案**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-142">When you've completed your article edits, scroll down and select **Propose file change**.</span></span>
6. <span data-ttu-id="9b0a1-143">次のページで、[ **プル要求の作成** ] を選択して、自動的に作成されたブランチを "マスター" にマージします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-143">On the next page, select **Create pull request** to merge your automatically created branch into 'master.'</span></span>
7. <span data-ttu-id="9b0a1-144">編集する次の記事に対して上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-144">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="9b0a1-145">既存のアーティクルの名前の変更または削除</span><span class="sxs-lookup"><span data-stu-id="9b0a1-145">Renaming or deleting an existing article</span></span>

<span data-ttu-id="9b0a1-146">既存のアーティクルの名前を変更または削除する場合は、必ずリダイレクトを追加してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-146">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="9b0a1-147">こうすることで、既存の記事へのリンクを持つユーザーは、引き続き適切な場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-147">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="9b0a1-148">リダイレクトは、リポジトリのルートにあるファイルの .openpublishing.redirection.jsによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-148">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="9b0a1-149">.openpublishing.redirection.jsにリダイレクトを追加するには、次のように、配列にエントリを追加し `redirections` ます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-149">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="9b0a1-150">`source_path`は、削除しようとしている古いアーティクルへの相対リポジトリパスです。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-150">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="9b0a1-151">パスがで始まり、で終わることを確認してください `mixed-reality-docs` `.md` 。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-151">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="9b0a1-152">は、 `redirect_url` 以前の記事から新しい記事までの相対パブリック URL です。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-152">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="9b0a1-153">この URL は、  `mixed-reality-docs` `.md` リポジトリパスではなくパブリック url を参照しているため、またはを含んでいないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-153">Be sure that this URL **doesn't** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="9b0a1-154">を使用した新しいアーティクル内のセクションへのリンク `#section` は許可されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-154">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="9b0a1-155">必要に応じて、ここで別のサイトへの絶対パスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-155">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="9b0a1-156">`redirect_document_id` 前のファイルのドキュメント ID を保持するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-156">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="9b0a1-157">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-157">The default is `false`.</span></span> <span data-ttu-id="9b0a1-158">リダイレクトされたアーティクルの属性値を保持する場合は、を使用し `true` `ms.documentid` ます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-158">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="9b0a1-159">ドキュメント ID を保持している場合は、ページビューやランキングなどのデータがターゲットアーティクルに転送されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-159">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="9b0a1-160">これは、リダイレクトが主に名前の変更であり、同じコンテンツの一部のみをカバーする別の記事へのポインターではない場合に実行します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-160">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="9b0a1-161">リダイレクトを追加する場合は、古いファイルも必ず削除してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-161">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="9b0a1-162">新しい記事を作成しています</span><span class="sxs-lookup"><span data-stu-id="9b0a1-162">Creating a new article</span></span>

<span data-ttu-id="9b0a1-163">次のワークフローを使用して、web ブラウザーで GitHub を使用してドキュメントリポジトリに *新しい記事を作成* します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-163">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="9b0a1-164">Microsoft Docs/mixed reality の "マスター" ブランチからフォークを作成します (右上の [ **フォーク** ] ボタンを使用します)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-164">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Master ブランチをフォークします。](images/forkbranch.png)
2. <span data-ttu-id="9b0a1-166">"Mixed-reality" フォルダーで、右上にある [ **新しいファイルの作成** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-166">In the "mixed-reality-docs" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="9b0a1-167">アーティクルのページ名を作成します (スペースの代わりにハイフンを使用し、句読点やアポストロフィは使用しません)。 "md" を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-167">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![新しいページの名前を指定します。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="9b0a1-169">必ず、"mixed-docs" フォルダー内から新しい記事を作成してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-169">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="9b0a1-170">これを確認するには、新しいファイル名の行で "/mixed-reality-docs/" を確認します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-170">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="9b0a1-171">新しいページの上部に、次のメタデータブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-171">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="9b0a1-172">[上記のセクション](#editing-an-existing-article)の手順に従って、関連するメタデータフィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-172">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="9b0a1-173">[Markdown の基礎](#markdown-basics)を使用して、記事の内容を記述します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-173">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="9b0a1-174">`## See also`記事の下部に、関連するその他の記事へのリンクが記載されたセクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-174">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="9b0a1-175">完了したら、[ **新しいファイルをコミット** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-175">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="9b0a1-176">[ **新しいプル要求** ] を選択し、フォークの ' master ' ブランチを microsoft docs/mixed reality ' マスター ' にマージします (矢印が正しい方法を指していることを確認します)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-176">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![フォークからのプル要求を作成して、Microsoft Docs/mixed reality に](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="9b0a1-178">Markdown の基本</span><span class="sxs-lookup"><span data-stu-id="9b0a1-178">Markdown basics</span></span>

<span data-ttu-id="9b0a1-179">Markdown 言語を使用してドキュメントを編集する方法については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-179">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="9b0a1-180">Markdown の基礎</span><span class="sxs-lookup"><span data-stu-id="9b0a1-180">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="9b0a1-181">Markdown リファレンスポスターの概要</span><span class="sxs-lookup"><span data-stu-id="9b0a1-181">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="9b0a1-182">Docs.microsoft.com の Markdown を作成するためのその他のリソース</span><span class="sxs-lookup"><span data-stu-id="9b0a1-182">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="9b0a1-183">テーブルの追加</span><span class="sxs-lookup"><span data-stu-id="9b0a1-183">Adding tables</span></span>

<span data-ttu-id="9b0a1-184">Docs.microsoft.com スタイルの表では、インライン CSS を試す場合でも、罫線やカスタムスタイルはありません。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-184">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="9b0a1-185">これは短時間は機能しているように見えますが、最終的には、プラットフォームによってテーブルからスタイルが除去されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-185">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="9b0a1-186">そのため、事前に計画し、テーブルを単純にしておきます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-186">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="9b0a1-187">[Markdown テーブルを簡単に作成できるサイトは次のように](https://www.tablesgenerator.com/markdown_tables)なります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-187">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="9b0a1-188">[Visual Studio Code の Docs Markdown 拡張機能](https://docs.microsoft.com/teamblog/docs-extension)では、 [Visual Studio Code (下記参照)](#using-visual-studio-code)を使用してドキュメントを編集する場合にも、テーブルの生成を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-188">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="9b0a1-189">追加 (イメージを)</span><span class="sxs-lookup"><span data-stu-id="9b0a1-189">Adding images</span></span>

<span data-ttu-id="9b0a1-190">リポジトリの "mixed-reality/images" フォルダーにイメージをアップロードし、記事で適切に参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-190">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="9b0a1-191">画像は自動的にフルサイズで表示されます。これは、大きな画像が記事全体の幅を占めることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-191">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="9b0a1-192">イメージをアップロードする前に、イメージのサイズを事前に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-192">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="9b0a1-193">推奨される幅は、600 ~ 700 ピクセルです。ただし、サイズの細かいスクリーンショットやスクリーンショットの一部である場合は、サイズを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-193">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9b0a1-194">マージする前に、フォークされたリポジトリにのみイメージをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-194">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="9b0a1-195">そのため、記事にイメージを追加する予定がある場合は、まず、 [Visual Studio Code を使用](#using-visual-studio-code) して、最初にそのイメージをフォークの "images" フォルダーに追加するか、web ブラウザーで次の操作を行っていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-195">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="9b0a1-196">Microsoft Docs/mixed reality リポジトリをフォークしています。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-196">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="9b0a1-197">フォーク内のアーティクルを編集しています。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-197">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="9b0a1-198">記事で参照しているイメージを、フォーク内の "mixed-reality/images" フォルダーにアップロードしました。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-198">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="9b0a1-199">フォークを Microsoft Docs/mixed reality の ' master ' ブランチにマージする **プル要求** を作成しました。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-199">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="9b0a1-200">独自にフォークしたリポジトリを設定する方法については、 [新しい記事を作成](#creating-a-new-article)するための手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-200">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="9b0a1-201">作業のプレビュー</span><span class="sxs-lookup"><span data-stu-id="9b0a1-201">Previewing your work</span></span>

<span data-ttu-id="9b0a1-202">Web ブラウザーを使用して GitHub で編集しているときに、ページの上部にある [ **プレビュー** ] タブを選択して、コミットする前に作業内容をプレビューすることができます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-202">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="9b0a1-203">review.docs.microsoft.com での変更のプレビューは、Microsoft の従業員のみが利用できます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-203">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="9b0a1-204">Microsoft の従業員: 投稿物が ' master ' ブランチにマージされたら、コンテンツをで公開する前にレビューすることができ https://review.docs.microsoft.com/windows/mixed-reality?branch=master ます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-204">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master.</span></span> <span data-ttu-id="9b0a1-205">左側の列の目次を使用して、記事を探します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-205">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="9b0a1-206">ブラウザーでの編集とデスクトップクライアントを使用した編集</span><span class="sxs-lookup"><span data-stu-id="9b0a1-206">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="9b0a1-207">クイック変更を行うには、ブラウザーでの編集が最も簡単な方法です。ただし、いくつかの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-207">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="9b0a1-208">スペルチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-208">You don't get spell-check.</span></span>
- <span data-ttu-id="9b0a1-209">他の記事へのスマートリンクは表示されません (記事のファイル名を手動で入力する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-209">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="9b0a1-210">イメージをアップロードして参照するのは面倒な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-210">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="9b0a1-211">これらの問題に対処しない場合は、貢献するときに、いくつかの[便利な拡張機能](#useful-extensions)を持つ[Visual Studio Code](https://code.visualstudio.com/)のようなデスクトップクライアントを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-211">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="9b0a1-212">Visual Studio Code の使用</span><span class="sxs-lookup"><span data-stu-id="9b0a1-212">Using Visual Studio Code</span></span>

<span data-ttu-id="9b0a1-213">[上記](#editing-in-the-browser-vs-editing-with-a-desktop-client)の理由から、デスクトップクライアントを使用して、web ブラウザーではなくドキュメントを編集することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-213">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="9b0a1-214">[Visual Studio Code](https://code.visualstudio.com/)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-214">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="9b0a1-215">セットアップ</span><span class="sxs-lookup"><span data-stu-id="9b0a1-215">Setup</span></span>

<span data-ttu-id="9b0a1-216">このリポジトリを使用するように Visual Studio Code を構成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-216">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="9b0a1-217">Web ブラウザーで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-217">In a web browser:</span></span>
    1. <span data-ttu-id="9b0a1-218">[PC の Git を](https://git-scm.com/downloads)インストールします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-218">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="9b0a1-219">[Visual Studio Code](https://code.visualstudio.com/) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-219">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="9b0a1-220">まだお持ちでない場合は、 [Microsoft docs/mixed reality をフォーク](#creating-a-new-article)します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-220">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="9b0a1-221">フォークで、[ **複製] または [ダウンロード** ] を選択し、URL をコピーします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-221">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="9b0a1-222">Visual Studio Code でフォークのローカル複製を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-222">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="9b0a1-223">[ **表示** ] メニューの [ **コマンドパレット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-223">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="9b0a1-224">「Git: Clone」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-224">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="9b0a1-225">コピーした URL を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-225">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="9b0a1-226">コンピューターの複製を保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-226">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="9b0a1-227">ポップアップで [ **リポジトリを開く** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-227">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="9b0a1-228">ドキュメントの編集</span><span class="sxs-lookup"><span data-stu-id="9b0a1-228">Editing documentation</span></span>

<span data-ttu-id="9b0a1-229">次のワークフローを使用して、Visual Studio Code でドキュメントに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-229">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="9b0a1-230">Visual Studio Code を使用する場合は、記事の [編集](#editing-an-existing-article) と [作成](#creating-a-new-article) に関するすべてのガイダンスと、上記の [Markdown の編集の基礎](#markdown-basics)が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-230">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="9b0a1-231">複製されたフォークが公式リポジトリを使用して最新の状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-231">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="9b0a1-232">Web ブラウザーでプル要求を作成して、Microsoft Docs/mixed reality ' master ' の他の共同作成者からの最近の変更をフォークに同期します (矢印が正しい方法であることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-232">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Microsoft Docs/mixed-reality からフォークへの変更の同期](images/sync_repos.PNG)
   2. <span data-ttu-id="9b0a1-234">Visual Studio Code で、[同期] ボタンを選択して、新しく更新されたフォークをローカルクローンに同期します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-234">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![[同期] ボタンの画像をクリックします。](images/sync_clone.png)
2. <span data-ttu-id="9b0a1-236">Visual Studio Code を使用して、複製されたリポジトリのアーティクルを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-236">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="9b0a1-237">1つ以上の記事を編集します (必要に応じて、画像を "images" フォルダーに追加します)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-237">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="9b0a1-238">変更を **エクスプローラー** に **保存** します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-238">**Save** changes in **Explorer**.</span></span>
      
      ![エクスプローラーで [すべてを保存] を選択します。](images/explorer_save.png)
   3. <span data-ttu-id="9b0a1-240">**ソース管理** ですべての変更を **コミット** します (メッセージが表示されたら書き込みコミットメッセージ)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-240">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![ソース管理で [すべてコミット] を選択する](images/source_control_commit.png)
   4. <span data-ttu-id="9b0a1-242">[ **同期** ] ボタンを選択して、変更内容を元に戻します (GitHub のフォーク)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-242">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![[同期] ボタンをクリックします。](images/sync_back.png)
3. <span data-ttu-id="9b0a1-244">Web ブラウザーでプル要求を作成して、フォークの新しい変更を Microsoft Docs/mixed reality ' マスター ' に戻します (矢印が正しい方法であることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-244">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![フォークからのプル要求を作成して、Microsoft Docs/mixed reality に](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="9b0a1-246">便利な拡張機能</span><span class="sxs-lookup"><span data-stu-id="9b0a1-246">Useful extensions</span></span>

<span data-ttu-id="9b0a1-247">ドキュメントを編集する際には、次の Visual Studio Code 拡張機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-247">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="9b0a1-248">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - **Alt + M キー** を使用して、次のような docs 作成オプションのメニューを表示します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-248">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="9b0a1-249">アップロードしたイメージを検索して参照します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-249">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="9b0a1-250">など、リスト、テーブル、ドキュメント固有の呼び出しなどの書式設定を追加 `>[!NOTE]` します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-250">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="9b0a1-251">内部リンクとブックマーク (ページ内の特定のセクションへのリンク) を検索して参照します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-251">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="9b0a1-252">書式設定エラーが強調表示されます (詳細については、エラーの上にマウスポインターを置きます)。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-252">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="9b0a1-253">[コードスペルチェッカー](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -スペルミスの単語に下線が引かれます。スペルミスの単語を右クリックして変更するか、辞書に保存します。</span><span class="sxs-lookup"><span data-stu-id="9b0a1-253">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
