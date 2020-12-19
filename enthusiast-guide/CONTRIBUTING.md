---
title: 関与する指示
description: Windows Mixed Reality 愛好家ガイドに貢献するための基本的な手順とガイドラインについて説明します。 フィードバック、編集、追加、およびヘルプをお待ちしています。
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: d8b4e23603a09d39fef076b600364a55410d12c3
ms.sourcegitcommit: 0b406ccbc7ce619e42809ba8dfdc47d83f4917ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97691397"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a><span data-ttu-id="3c011-105">Mixed Reality 愛好ガイドへの貢献</span><span class="sxs-lookup"><span data-stu-id="3c011-105">Contributing to the Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="3c011-106">このガイドに関心をお寄せいただき、ありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="3c011-106">Thank you for your interest in the Enthusiast Guide.</span></span> <span data-ttu-id="3c011-107">お客様からのフィードバック、編集、追加、ドキュメントの改善にご協力いただき、ありがとうございます。このページでは、貢献するための基本的な手順とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3c011-107">We appreciate your feedback, edits, additions and help with improving our docs. This page covers the basic steps and guidelines for contributing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c011-108">docs.microsoft.com に公開されるすべてのリポジトリには、「[Microsoft Open Source Code of Conduct (Microsoft オープンソース倫理規定)](https://opensource.microsoft.com/codeofconduct/)」が適用されています。</span><span class="sxs-lookup"><span data-stu-id="3c011-108">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="3c011-109">詳細については、[倫理規定についてのよくある質問](https://opensource.microsoft.com/codeofconduct/faq/)に関するページをご覧いただくか、[opencode@microsoft.com](mailto:opencode@microsoft.com) 宛てに質問またはコメントを送信してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-109">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any questions or comments.</span></span><br>
>
> <span data-ttu-id="3c011-110">パブリック リポジトリにあるドキュメントおよびコード例に対する軽微な修正や明確化は、「[docs.microsoft.com - 使用条件](https://docs.microsoft.com/legal/termsofuse)」の対象になります。</span><span class="sxs-lookup"><span data-stu-id="3c011-110">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the [docs.microsoft.com Terms of Use](https://docs.microsoft.com/legal/termsofuse).</span></span> <span data-ttu-id="3c011-111">Microsoft の従業員ではない共同作成者が新規または大幅な変更を行うと、オンライン貢献者使用許諾契約書 (CLA) の提出をお願いするコメントが pull request 内に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-111">New or significant changes will generate a comment in the pull request asking you to submit an online Contribution License Agreement (CLA) if you are not an employee of Microsoft.</span></span> <span data-ttu-id="3c011-112">pull request が正しく受理されるように、オンライン フォームへのご記入をお願いいたします。</span><span class="sxs-lookup"><span data-stu-id="3c011-112">We need you to complete the online form before we can accept your pull request.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="3c011-113">開始する前に</span><span class="sxs-lookup"><span data-stu-id="3c011-113">Before you start</span></span>

<span data-ttu-id="3c011-114">まだお持ちでない場合は、 [GitHub アカウントを作成](https://github.com/join)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-114">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="3c011-115">Microsoft の従業員の場合は、microsoft [オープンソースポータル](https://repos.opensource.microsoft.com/)で GitHub アカウントを microsoft エイリアスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="3c011-115">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="3c011-116">**"Microsoft"** と "microsoft **docs"** の組織に参加してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-116">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="3c011-117">GitHub アカウントを設定するときは、次のセキュリティに関する注意事項もお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c011-117">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="3c011-118">[Github アカウントの強力なパスワード](https://github.com/settings/admin)を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c011-118">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="3c011-119">[2 要素認証](https://github.com/settings/two_factor_authentication/configure)を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3c011-119">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="3c011-120">[回復コード](https://github.com/settings/auth/recovery-codes)を安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="3c011-120">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="3c011-121">[パブリックプロファイルの設定](https://github.com/settings/profile)を更新します。</span><span class="sxs-lookup"><span data-stu-id="3c011-121">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="3c011-122">自分の名前を設定し、電子メールアドレスを *表示しない* ように *パブリック電子メール* を設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-122">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="3c011-123">プロフィール画像をアップロードすることをお勧めします。これは、投稿するドキュメントページにサムネイルが表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="3c011-123">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="3c011-124">コマンドラインを使用する場合は、 [Windows 用の Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)を設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-124">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="3c011-125">これにより、投稿を行うたびにパスワードを入力する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c011-125">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="3c011-126">発行システムは GitHub に関連付けられているため、これらの手順は重要です。</span><span class="sxs-lookup"><span data-stu-id="3c011-126">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="3c011-127">GitHub エイリアスを使用して、各記事の作成者または共同作成者として一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-127">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="how-to-make-a-change"></a><span data-ttu-id="3c011-128">変更する方法</span><span class="sxs-lookup"><span data-stu-id="3c011-128">How to make a change</span></span>

| <span data-ttu-id="3c011-129">ドキュメントへの変更を提案するには、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="3c011-129">To suggest a change to the docs, follow these steps:</span></span> | <span data-ttu-id="3c011-130">Screenshots (スクリーンショット)</span><span class="sxs-lookup"><span data-stu-id="3c011-130">Screenshots</span></span> |
| :------------------- | :--------: |
| <span data-ttu-id="3c011-131">1. Docs.microsoft.com ページを表示している場合は、ページの右上にある [ **編集** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c011-131">1. If you're viewing a Docs.microsoft.com page, click the **Edit** button in the upper right of the page.</span></span>  <span data-ttu-id="3c011-132">[GitHub リポジトリ](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)内の対応するマークダウン ソース ファイルにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="3c011-132">You will be redirected to the corresponding Markdown source file in the [GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide).</span></span> | ![[編集] ボタン](images/edit_button.jpg) |
| <span data-ttu-id="3c011-134">2. まだ GitHub アカウントを持っていない場合は、右上にある [ **サインアップ** ] をクリックして新しいアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c011-134">2. If you don't already have a GitHub account, click **Sign Up** in the upper right and create a new account.</span></span> | ![サインアップボタン](images/signup-for-github-button.png)|
| <span data-ttu-id="3c011-136">3. 対応する GitHub ページが開いたら、[編集] (鉛筆アイコン) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c011-136">3. On the corresponding GitHub page that opens, click Edit (the pencil icon).</span></span> | ![鉛筆ボタン](images/pencil_button.jpg)|
| <span data-ttu-id="3c011-138">4. [ファイルの編集] ウィンドウで、 [ファイルのメタデータを更新](#updating-metadata) し、Markdown 言語を使用してコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="3c011-138">4. In the Edit file pane, [update the files metadata](#updating-metadata) and use Markdown language to change the content.</span></span> <span data-ttu-id="3c011-139">([Markdown を記述する方法](https://help.github.com/articles/basic-writing-and-formatting-syntax/))</span><span class="sxs-lookup"><span data-stu-id="3c011-139">([How to write markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))</span></span>| ![ファイルの編集](images/edit-in-github.png)|
| <span data-ttu-id="3c011-141">5. [変更のプレビュー] をクリックして、書式設定が想定どおりに表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c011-141">5. Click Preview changes to verify the formatting looks as expected.</span></span> | ![変更のプレビュー](images/edit-in-github.png)|
| <span data-ttu-id="3c011-143">6. 完了したら、ページの一番下までスクロールし、[ファイルの変更の提案] をクリックすると、[変更の比較] ページが表示され、変更を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3c011-143">6. When you're done, scroll to the bottom of the page and click "Propose file change", you will be presented with a "Comparing changes" page, allowing you to verify your changes.</span></span> <span data-ttu-id="3c011-144">次に、[プル要求の作成] ボタンをクリックして、変更を送信します。</span><span class="sxs-lookup"><span data-stu-id="3c011-144">Then click the "Create pull request" button to submit your changes.</span></span> <span data-ttu-id="3c011-145">これで完了です。</span><span class="sxs-lookup"><span data-stu-id="3c011-145">At this point you are finished!</span></span> | ![変更を提案する](images/propose.jpg)|

<span data-ttu-id="3c011-147">(プル要求を使用して) 変更を送信した後は、ドキュメントチームのメンバーによってレビューされます。</span><span class="sxs-lookup"><span data-stu-id="3c011-147">After you submit changes (via a pull request), they will be reviewed by a member of the documentation team.</span></span> <span data-ttu-id="3c011-148">要求が受け入れられた場合、更新プログラムはに発行され [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) ます。</span><span class="sxs-lookup"><span data-stu-id="3c011-148">If your request is accepted, updates are published to [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="3c011-149">\* 内部レビューのみの場合は、で変更を確認でき [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) ます。</span><span class="sxs-lookup"><span data-stu-id="3c011-149">\*For internal review only, you can see your changes at [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master).</span></span>

### <a name="updating-metadata"></a><span data-ttu-id="3c011-150">メタデータの更新</span><span class="sxs-lookup"><span data-stu-id="3c011-150">Updating Metadata</span></span>

<span data-ttu-id="3c011-151">各記事の上部にあるメタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="3c011-151">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="3c011-152">**title**: 記事が表示されているときに [ブラウザー] タブに表示されるページタイトル。</span><span class="sxs-lookup"><span data-stu-id="3c011-152">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="3c011-153">ページタイトルは、SEO とインデックス作成に使用されるため、必要な場合以外はタイトルを変更しないでください (ただし、ドキュメントが公開される前には重要度が低くなります)。</span><span class="sxs-lookup"><span data-stu-id="3c011-153">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="3c011-154">**description**: 記事のコンテンツに関する簡単な説明を記述します。これにより、SEO と検出が向上します。</span><span class="sxs-lookup"><span data-stu-id="3c011-154">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="3c011-155">**author**: ページのプライマリ所有者である場合は、ここに GitHub エイリアスを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c011-155">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="3c011-156">**ms. author**: ページのプライマリ所有者である場合は、ここに Microsoft エイリアスを追加します (必要なのはエイリアスではありません @microsoft.com )。</span><span class="sxs-lookup"><span data-stu-id="3c011-156">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="3c011-157">**ms. date**: ページに主要なコンテンツを追加する場合は日付を更新します。ただし、明確、書式設定、文法、スペルなどの修正には使用しません。</span><span class="sxs-lookup"><span data-stu-id="3c011-157">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="3c011-158">**キーワード**: キーワードは、SEO (検索エンジンの最適化) に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3c011-158">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="3c011-159">コンマとスペースで区切られたキーワードを追加します。これは、記事に固有のものですが、リスト内の最後のキーワードの後には句読点がありません。</span><span class="sxs-lookup"><span data-stu-id="3c011-159">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="3c011-160">すべての記事に適用するグローバルキーワードを追加する必要はありません。他の場所で管理されているためです。</span><span class="sxs-lookup"><span data-stu-id="3c011-160">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 

### <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="3c011-161">既存のアーティクルの名前の変更または削除</span><span class="sxs-lookup"><span data-stu-id="3c011-161">Renaming or deleting an existing article</span></span>

<span data-ttu-id="3c011-162">既存のアーティクルの名前を変更または削除する場合は、必ずリダイレクトを追加してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-162">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="3c011-163">こうすることで、既存の記事へのリンクを持つユーザーは、引き続き適切な場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-163">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="3c011-164">リダイレクトは、リポジトリのルートにあるファイルの .openpublishing.redirection.jsによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-164">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="3c011-165">.openpublishing.redirection.jsにリダイレクトを追加するには、次のように、配列にエントリを追加し `redirections` ます。</span><span class="sxs-lookup"><span data-stu-id="3c011-165">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="3c011-166">`source_path`は、削除しようとしている古いアーティクルへの相対リポジトリパスです。</span><span class="sxs-lookup"><span data-stu-id="3c011-166">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="3c011-167">パスがで始まり、で終わることを確認してください `mixed-reality-docs/enthusiast-guide` `.md` 。</span><span class="sxs-lookup"><span data-stu-id="3c011-167">Be sure the path starts with `mixed-reality-docs/enthusiast-guide` and ends with `.md`.</span></span>
- <span data-ttu-id="3c011-168">は、 `redirect_url` 以前の記事から新しい記事までの相対パブリック URL です。</span><span class="sxs-lookup"><span data-stu-id="3c011-168">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="3c011-169">この URL は、  `mixed-reality-docs/enthusiast-guide` `.md` リポジトリパスではなくパブリック url を参照しているため、またはを含んでいないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-169">Be sure that this URL **doesn't** contain `mixed-reality-docs/enthusiast-guide` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="3c011-170">を使用した新しいアーティクル内のセクションへのリンク `#section` は許可されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-170">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="3c011-171">必要に応じて、ここで別のサイトへの絶対パスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3c011-171">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="3c011-172">`redirect_document_id` 前のファイルのドキュメント ID を保持するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3c011-172">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="3c011-173">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="3c011-173">The default is `false`.</span></span> <span data-ttu-id="3c011-174">リダイレクトされたアーティクルの属性値を保持する場合は、を使用し `true` `ms.documentid` ます。</span><span class="sxs-lookup"><span data-stu-id="3c011-174">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="3c011-175">ドキュメント ID を保持している場合は、ページビューやランキングなどのデータがターゲットアーティクルに転送されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-175">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="3c011-176">これは、リダイレクトが主に名前の変更であり、同じコンテンツの一部のみをカバーする別の記事へのポインターではない場合に実行します。</span><span class="sxs-lookup"><span data-stu-id="3c011-176">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="3c011-177">リダイレクトを追加する場合は、古いファイルも必ず削除してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-177">If you add a redirect, be sure to delete the old file as well.</span></span>

### <a name="creating-a-new-article"></a><span data-ttu-id="3c011-178">新しい記事を作成しています</span><span class="sxs-lookup"><span data-stu-id="3c011-178">Creating a new article</span></span>

<span data-ttu-id="3c011-179">次のワークフローを使用して、web ブラウザーで GitHub を使用してドキュメントリポジトリに *新しい記事を作成* します。</span><span class="sxs-lookup"><span data-stu-id="3c011-179">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="3c011-180">(右上の [ **フォーク** ] ボタンを使用して) microsoft docs/mixed-reality/tree/docs/愛好家ガイドの "マスター" ブランチからフォークを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c011-180">Create a fork off the MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Master ブランチをフォークします。](images/forkbranch.png)
2. <span data-ttu-id="3c011-182">[Mixed-reality] フォルダーで、右上にある [ **新しいファイルの作成** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c011-182">In the "mixed-reality/enthusiast-guide" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="3c011-183">アーティクルのページ名を作成します (スペースの代わりにハイフンを使用し、句読点やアポストロフィは使用しません)。 "md" を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c011-183">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![新しいページの名前を指定します。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="3c011-185">必ず、"mixed-docs/愛好" フォルダー内から新しい記事を作成してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-185">Make sure you create the new article from within the "mixed-reality-docs/enthusiast" folder.</span></span> <span data-ttu-id="3c011-186">これを確認するには、新しいファイル名の行で "/mixed-reality-docs/enthusiast-guide" を確認します。</span><span class="sxs-lookup"><span data-stu-id="3c011-186">You can confirm this by checking for "/mixed-reality-docs/enthusiast-guide" in the new file name line.</span></span>

4. <span data-ttu-id="3c011-187">新しいページの上部に、次のメタデータブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c011-187">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="3c011-188">[上記のセクション](#updating-metadata)の手順に従って、関連するメタデータフィールドを入力します。</span><span class="sxs-lookup"><span data-stu-id="3c011-188">Fill in the relevant metadata fields per the instructions in the [section above](#updating-metadata).</span></span>
6. <span data-ttu-id="3c011-189">[Markdown の基礎](#markdown-basics)を使用して、記事の内容を記述します。</span><span class="sxs-lookup"><span data-stu-id="3c011-189">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="3c011-190">`## See also`記事の下部に、関連するその他の記事へのリンクが記載されたセクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c011-190">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="3c011-191">完了したら、[ **新しいファイルをコミット** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c011-191">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="3c011-192">[ **新しいプル要求** ] を選択し、フォークの ' master ' ブランチを microsoft docs/mixed-reality/愛好家ガイド ' マスター ' にマージします (矢印が正しい方法であることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="3c011-192">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality/enthusiast-guide 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![フォークからプル要求を作成して、Microsoft Docs/mixed-現実ガイドに](images/pr_to_master.PNG)

## <a name="working-with-branches"></a><span data-ttu-id="3c011-194">ブランチを操作する</span><span class="sxs-lookup"><span data-stu-id="3c011-194">Working with Branches</span></span>

<span data-ttu-id="3c011-195">2つの主要な親分岐 ([マスター](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)) を使用するのは、 [Mixed Reality のガイド GitHub リポジトリ](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)です。このコンテンツ[は、](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)[ライブサイト](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)で表示されるコンテンツの[ステージングサイト](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="3c011-195">The [Mixed Reality Enthusiast Guide GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utilizes two main parent branches: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), this content can be reviewed on the [staging site](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide), and [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), for content appearing on the [live site](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="3c011-196">投稿を作成するときは、プル要求 (PR) を **Master** ブランチに送信してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-196">When making contributions, please submit your Pull Request (PR) to the **Master** branch.</span></span> <span data-ttu-id="3c011-197">このブランチはステージング サイトで表示でき、ライブで公開する準備ができている投稿のみを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="3c011-197">This branch can be viewed on the staging site and should only contain contributions that are ready to be published live.</span></span> <span data-ttu-id="3c011-198">また、独自の一意のブランチ名を使用してブランチを作成し、送信することもできます。これは、ステージングサイトで選択して表示できます。</span><span class="sxs-lookup"><span data-stu-id="3c011-198">You may also create and submit a branch with your own unique branch name which can be selected and viewed in the staging site.</span></span> <span data-ttu-id="3c011-199">( **ライブ** ブランチは、コンテンツ管理者のみが使用できます)。</span><span class="sxs-lookup"><span data-stu-id="3c011-199">(The **Live** branch is only allowed for use by the content administrators.)</span></span>

## <a name="markdown-basics"></a><span data-ttu-id="3c011-200">Markdown の基本</span><span class="sxs-lookup"><span data-stu-id="3c011-200">Markdown basics</span></span>

<span data-ttu-id="3c011-201">Markdown 言語を使用してドキュメントを編集する方法については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c011-201">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="3c011-202">Markdown の基礎</span><span class="sxs-lookup"><span data-stu-id="3c011-202">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="3c011-203">Markdown リファレンスポスターの概要</span><span class="sxs-lookup"><span data-stu-id="3c011-203">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="3c011-204">Docs.microsoft.com の Markdown を作成するためのその他のリソース</span><span class="sxs-lookup"><span data-stu-id="3c011-204">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="3c011-205">テーブルの追加</span><span class="sxs-lookup"><span data-stu-id="3c011-205">Adding tables</span></span>

<span data-ttu-id="3c011-206">Docs.microsoft.com スタイルの表では、インライン CSS を試す場合でも、罫線やカスタムスタイルはありません。</span><span class="sxs-lookup"><span data-stu-id="3c011-206">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="3c011-207">これは短時間は機能しているように見えますが、最終的には、プラットフォームによってテーブルからスタイルが除去されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-207">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="3c011-208">そのため、事前に計画し、テーブルを単純にしておきます。</span><span class="sxs-lookup"><span data-stu-id="3c011-208">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="3c011-209">[Markdown テーブルを簡単に作成できるサイトは次のように](https://www.tablesgenerator.com/markdown_tables)なります。</span><span class="sxs-lookup"><span data-stu-id="3c011-209">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="3c011-210">[Visual Studio Code の Docs Markdown 拡張機能](https://docs.microsoft.com/teamblog/docs-extension)では、 [Visual Studio Code (下記参照)](#using-visual-studio-code)を使用してドキュメントを編集する場合にも、テーブルの生成を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3c011-210">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="3c011-211">追加 (イメージを)</span><span class="sxs-lookup"><span data-stu-id="3c011-211">Adding images</span></span>

<span data-ttu-id="3c011-212">リポジトリの "mixed-reality/images" フォルダーにイメージをアップロードし、記事で適切に参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-212">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="3c011-213">画像は自動的にフルサイズで表示されます。これは、大きな画像が記事全体の幅を占めることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3c011-213">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="3c011-214">イメージをアップロードする前に、イメージのサイズを事前に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c011-214">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="3c011-215">推奨される幅は、600 ~ 700 ピクセルです。ただし、サイズの細かいスクリーンショットやスクリーンショットの一部である場合は、サイズを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-215">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3c011-216">マージする前に、フォークされたリポジトリにのみイメージをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="3c011-216">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="3c011-217">そのため、記事にイメージを追加する予定がある場合は、まず、 [Visual Studio Code を使用](#using-visual-studio-code) して、最初にそのイメージをフォークの "images" フォルダーに追加するか、web ブラウザーで次の操作を行っていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-217">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="3c011-218">Microsoft Docs/mixed reality リポジトリをフォークしています。</span><span class="sxs-lookup"><span data-stu-id="3c011-218">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="3c011-219">フォーク内のアーティクルを編集しています。</span><span class="sxs-lookup"><span data-stu-id="3c011-219">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="3c011-220">記事で参照しているイメージを、フォーク内の "mixed-reality/images" フォルダーにアップロードしました。</span><span class="sxs-lookup"><span data-stu-id="3c011-220">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="3c011-221">フォークを Microsoft Docs/mixed reality の ' master ' ブランチにマージする **プル要求** を作成しました。</span><span class="sxs-lookup"><span data-stu-id="3c011-221">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="3c011-222">独自にフォークしたリポジトリを設定する方法については、 [新しい記事を作成](#creating-a-new-article)するための手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="3c011-222">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="3c011-223">作業のプレビュー</span><span class="sxs-lookup"><span data-stu-id="3c011-223">Previewing your work</span></span>

<span data-ttu-id="3c011-224">Web ブラウザーを使用して GitHub で編集しているときに、ページの上部にある [ **プレビュー** ] タブを選択して、コミットする前に作業内容をプレビューすることができます。</span><span class="sxs-lookup"><span data-stu-id="3c011-224">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="3c011-225">review.docs.microsoft.com での変更のプレビューは、Microsoft の従業員のみが利用できます。</span><span class="sxs-lookup"><span data-stu-id="3c011-225">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="3c011-226">Microsoft の従業員: 投稿物が ' master ' ブランチにマージされたら、コンテンツをで公開する前にレビューすることができ https://review.docs.microsoft.com/windows/mixed-reality?branch=master ます。</span><span class="sxs-lookup"><span data-stu-id="3c011-226">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master.</span></span> <span data-ttu-id="3c011-227">左側の列の目次を使用して、記事を探します。</span><span class="sxs-lookup"><span data-stu-id="3c011-227">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="3c011-228">ブラウザーでの編集とデスクトップクライアントを使用した編集</span><span class="sxs-lookup"><span data-stu-id="3c011-228">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="3c011-229">クイック変更を行うには、ブラウザーでの編集が最も簡単な方法です。ただし、いくつかの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-229">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="3c011-230">スペルチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="3c011-230">You don't get spell-check.</span></span>
- <span data-ttu-id="3c011-231">他の記事へのスマートリンクは表示されません (記事のファイル名を手動で入力する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="3c011-231">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="3c011-232">イメージをアップロードして参照するのは面倒な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c011-232">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="3c011-233">これらの問題に対処しない場合は、貢献するときに、いくつかの[便利な拡張機能](#useful-extensions)を持つ[Visual Studio Code](https://code.visualstudio.com/)のようなデスクトップクライアントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c011-233">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="3c011-234">Visual Studio Code の使用</span><span class="sxs-lookup"><span data-stu-id="3c011-234">Using Visual Studio Code</span></span>

<span data-ttu-id="3c011-235">[上記](#editing-in-the-browser-vs-editing-with-a-desktop-client)の理由から、デスクトップクライアントを使用して、web ブラウザーではなくドキュメントを編集することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c011-235">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="3c011-236">[Visual Studio Code](https://code.visualstudio.com/)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c011-236">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="3c011-237">セットアップ</span><span class="sxs-lookup"><span data-stu-id="3c011-237">Setup</span></span>

<span data-ttu-id="3c011-238">このリポジトリを使用するように Visual Studio Code を構成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3c011-238">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="3c011-239">Web ブラウザーで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="3c011-239">In a web browser:</span></span>
    1. <span data-ttu-id="3c011-240">[PC の Git を](https://git-scm.com/downloads)インストールします。</span><span class="sxs-lookup"><span data-stu-id="3c011-240">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="3c011-241">[Visual Studio Code](https://code.visualstudio.com/) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3c011-241">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="3c011-242">まだお持ちでない場合は、 [Microsoft docs/mixed reality をフォーク](#creating-a-new-article)します。</span><span class="sxs-lookup"><span data-stu-id="3c011-242">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="3c011-243">フォークで、[ **複製] または [ダウンロード** ] を選択し、URL をコピーします。</span><span class="sxs-lookup"><span data-stu-id="3c011-243">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="3c011-244">Visual Studio Code でフォークのローカル複製を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c011-244">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="3c011-245">[ **表示** ] メニューの [ **コマンドパレット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c011-245">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="3c011-246">「Git: Clone」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3c011-246">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="3c011-247">コピーした URL を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3c011-247">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="3c011-248">コンピューターの複製を保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c011-248">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="3c011-249">ポップアップで [ **リポジトリを開く** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c011-249">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="3c011-250">ドキュメントの編集</span><span class="sxs-lookup"><span data-stu-id="3c011-250">Editing documentation</span></span>

<span data-ttu-id="3c011-251">次のワークフローを使用して、Visual Studio Code でドキュメントに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="3c011-251">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="3c011-252">Visual Studio Code を使用する場合は、記事の [編集](#how-to-make-a-change) と [作成](#creating-a-new-article) に関するすべてのガイダンスと、上記の [Markdown の編集の基礎](#markdown-basics)が適用されます。</span><span class="sxs-lookup"><span data-stu-id="3c011-252">All the guidance for [editing](#how-to-make-a-change) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="3c011-253">複製されたフォークが公式リポジトリを使用して最新の状態であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c011-253">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="3c011-254">Web ブラウザーでプル要求を作成して、Microsoft Docs/mixed reality ' master ' の他の共同作成者からの最近の変更をフォークに同期します (矢印が正しい方法であることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="3c011-254">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Microsoft Docs/mixed-reality からフォークへの変更の同期](images/sync_repos.PNG)
   2. <span data-ttu-id="3c011-256">Visual Studio Code で、[同期] ボタンを選択して、新しく更新されたフォークをローカルクローンに同期します。</span><span class="sxs-lookup"><span data-stu-id="3c011-256">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![[同期] ボタンの画像をクリックします。](images/sync_clone.png)
2. <span data-ttu-id="3c011-258">Visual Studio Code を使用して、複製されたリポジトリのアーティクルを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="3c011-258">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="3c011-259">1つ以上の記事を編集します (必要に応じて、画像を "images" フォルダーに追加します)。</span><span class="sxs-lookup"><span data-stu-id="3c011-259">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="3c011-260">変更を **エクスプローラー** に **保存** します。</span><span class="sxs-lookup"><span data-stu-id="3c011-260">**Save** changes in **Explorer**.</span></span>
      
      ![エクスプローラーで [すべてを保存] を選択します。](images/explorer_save.png)
   3. <span data-ttu-id="3c011-262">**ソース管理** ですべての変更を **コミット** します (メッセージが表示されたら書き込みコミットメッセージ)。</span><span class="sxs-lookup"><span data-stu-id="3c011-262">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![ソース管理で [すべてコミット] を選択する](images/source_control_commit.png)
   4. <span data-ttu-id="3c011-264">[ **同期** ] ボタンを選択して、変更内容を元に戻します (GitHub のフォーク)。</span><span class="sxs-lookup"><span data-stu-id="3c011-264">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![[同期] ボタンをクリックします。](images/sync_back.png)
3. <span data-ttu-id="3c011-266">Web ブラウザーでプル要求を作成して、フォークの新しい変更を Microsoft Docs/mixed reality ' マスター ' に戻します (矢印が正しい方法であることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="3c011-266">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![フォークからのプル要求を作成して、Microsoft Docs/mixed reality に](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="3c011-268">便利な拡張機能</span><span class="sxs-lookup"><span data-stu-id="3c011-268">Useful extensions</span></span>

<span data-ttu-id="3c011-269">ドキュメントを編集する際には、次の Visual Studio Code 拡張機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3c011-269">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="3c011-270">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - **Alt + M キー** を使用して、次のような docs 作成オプションのメニューを表示します。</span><span class="sxs-lookup"><span data-stu-id="3c011-270">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="3c011-271">アップロードしたイメージを検索して参照します。</span><span class="sxs-lookup"><span data-stu-id="3c011-271">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="3c011-272">など、リスト、テーブル、ドキュメント固有の呼び出しなどの書式設定を追加 `>[!NOTE]` します。</span><span class="sxs-lookup"><span data-stu-id="3c011-272">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="3c011-273">内部リンクとブックマーク (ページ内の特定のセクションへのリンク) を検索して参照します。</span><span class="sxs-lookup"><span data-stu-id="3c011-273">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="3c011-274">書式設定エラーが強調表示されます (詳細については、エラーの上にマウスポインターを置きます)。</span><span class="sxs-lookup"><span data-stu-id="3c011-274">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="3c011-275">[コードスペルチェッカー](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -スペルミスの単語に下線が引かれます。スペルミスの単語を右クリックして変更するか、辞書に保存します。</span><span class="sxs-lookup"><span data-stu-id="3c011-275">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a><span data-ttu-id="3c011-276">Windows Mixed Reality 愛好ガイドに関するフィードバックを提供するための問題の使用</span><span class="sxs-lookup"><span data-stu-id="3c011-276">Using issues to provide feedback on Windows Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="3c011-277">フィードバックを提供したり、問題を指摘したりするには、実際のドキュメントページを直接変更するのではなく、問題を [作成](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) します。コンテンツの所有者は、問題を適切なタイミングで解決するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="3c011-277">To provide feedback, or point out a problem, rather than directly modifying actual documentation pages, [create an issue](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) and the content owners will do their best to address the issue in a timely fashion.</span></span>

<span data-ttu-id="3c011-278">特定のページに関する問題を作成する場合は、トピックタイトルと URL を必ず含めてください。</span><span class="sxs-lookup"><span data-stu-id="3c011-278">Be sure to include the topic title and the URL if you are creating an issue regarding a specific page.</span></span>

<span data-ttu-id="3c011-279">このコンテンツをサポートしていただき、ありがとうございます。</span><span class="sxs-lookup"><span data-stu-id="3c011-279">Thank you for supporting this content!</span></span>
