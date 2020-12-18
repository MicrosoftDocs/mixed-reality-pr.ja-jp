---
title: 関与する指示
description: GitHub-flavored Markdown を使用して、docs.microsoft.com プラットフォームで Mixed Reality 開発者ドキュメントに投稿する方法について説明します。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: dd84ba86af0b86b29510c4c317ad0a14fabc296b
ms.sourcegitcommit: 3762d207d3b5f4a1d932197aae7a4fae4baec960
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97676265"
---
# <a name="contributing-to-mixed-reality-developer-documentation"></a>Mixed Reality 開発者向けドキュメントへの貢献

[Mixed Reality 開発者向けドキュメントのパブリックリポジトリ](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)へようこそ。 このリポジトリで作成または編集した記事 **は、パブリックに表示されます。** 

Mixed Reality ドキュメントは現在、docs.microsoft.com プラットフォームにあります。これは、flavored Markdown を Markdig 特徴と共に使用します。 このリポジトリで編集するコンテンツは、に表示される定型ページに書式設定され https://docs.microsoft.com/windows/mixed-reality ます。 HoloLens または VR のドキュメントに投稿する場合は、それぞれの [hololens](https://github.com/MicrosoftDocs/Hololens) および [vr](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) リポジトリを参照してください。

このページでは、Markdown の基本に寄与するための基本的な手順とガイドラインについて説明します。 投稿いただき、ありがとうございます。

## <a name="before-you-start"></a>開始する前に

まだお持ちでない場合は、 [GitHub アカウントを作成](https://github.com/join)する必要があります。

>[!NOTE]
>Microsoft の従業員の場合は、microsoft [オープンソースポータル](https://repos.opensource.microsoft.com/)で GitHub アカウントを microsoft エイリアスにリンクします。 **"Microsoft"** と "microsoft **docs"** の組織に参加してください。

GitHub アカウントを設定するときは、次のセキュリティに関する注意事項もお勧めします。
- [Github アカウントの強力なパスワード](https://github.com/settings/admin)を作成します。
- [2 要素認証](https://github.com/settings/two_factor_authentication/configure)を有効にします。
- [回復コード](https://github.com/settings/auth/recovery-codes)を安全な場所に保存します。
- [パブリックプロファイルの設定](https://github.com/settings/profile)を更新します。
   - 自分の名前を設定し、電子メールアドレスを *表示しない* ように *パブリック電子メール* を設定することを検討してください。
   - プロフィール画像をアップロードすることをお勧めします。これは、投稿するドキュメントページにサムネイルが表示されるためです。
- コマンドラインを使用する場合は、 [Windows 用の Git Credential Manager](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)を設定することを検討してください。 これにより、投稿を行うたびにパスワードを入力する必要がなくなります。

発行システムは GitHub に関連付けられているため、これらの手順は重要です。 GitHub エイリアスを使用して、各記事の作成者または共同作成者として一覧表示されます。

## <a name="editing-an-existing-article"></a>既存の記事の編集

次のワークフローを使用して、web ブラウザーで GitHub 経由で *既存の記事* の更新を行います。

1. "Mixed-reality" フォルダーで、編集する記事に移動します。
2. 右上の [編集] ボタン (鉛筆アイコン) を選択すると、"マスター" 分岐から破棄可能な分岐が自動的にフォークされます。

   ![記事を編集します。](images/editpage.png)
3. [「Markdown の基礎」](#markdown-basics)に従って、記事の内容を編集します。
4. 各記事の上部にあるメタデータを更新します。
   * title: 記事が表示されているときに [ブラウザー] タブに表示されるページタイトル。 ページタイトルは、SEO とインデックス作成に使用されるため、必要な場合以外はタイトルを変更しないでください (ただし、ドキュメントが公開される前には重要度が低くなります)。
   * description: 記事のコンテンツに関する簡単な説明を記述します。これにより、SEO と検出が向上します。
   * author: ページのプライマリ所有者である場合は、ここに GitHub エイリアスを追加します。
   * ms. author: ページのプライマリ所有者である場合は、ここに Microsoft エイリアスを追加します (必要なのはエイリアスではありません @microsoft.com )。
   * ms. date: ページに主要なコンテンツを追加する場合は日付を更新します。ただし、明確、書式設定、文法、スペルなどの修正には使用しません。
   * キーワード: キーワードは、SEO (検索エンジンの最適化) に役立ちます。 コンマとスペースで区切られたキーワードを追加します。これは、記事に固有のものですが、リスト内の最後のキーワードの後には句読点がありません。 すべての記事に適用するグローバルキーワードを追加する必要はありません。他の場所で管理されているためです。 
5. 記事の編集が完了したら、下にスクロールして [ **ファイル変更の提案**] を選択します。
6. 次のページで、[ **プル要求の作成** ] を選択して、自動的に作成されたブランチを "マスター" にマージします。
7. 編集する次の記事に対して上記の手順を繰り返します。

## <a name="renaming-or-deleting-an-existing-article"></a>既存のアーティクルの名前の変更または削除

既存のアーティクルの名前を変更または削除する場合は、必ずリダイレクトを追加してください。 こうすることで、既存の記事へのリンクを持つユーザーは、引き続き適切な場所に配置されます。 リダイレクトは、リポジトリのルートにあるファイルの .openpublishing.redirection.jsによって管理されます。

.openpublishing.redirection.jsにリダイレクトを追加するには、次のように、配列にエントリを追加し `redirections` ます。

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`は、削除しようとしている古いアーティクルへの相対リポジトリパスです。 パスがで始まり、で終わることを確認してください `mixed-reality-docs` `.md` 。
- は、 `redirect_url` 以前の記事から新しい記事までの相対パブリック URL です。 この URL は、  `mixed-reality-docs` `.md` リポジトリパスではなくパブリック url を参照しているため、またはを含んでいないことを確認してください。 を使用した新しいアーティクル内のセクションへのリンク `#section` は許可されます。 必要に応じて、ここで別のサイトへの絶対パスを使用することもできます。
- `redirect_document_id` 前のファイルのドキュメント ID を保持するかどうかを示します。 既定値は、`false` です。 リダイレクトされたアーティクルの属性値を保持する場合は、を使用し `true` `ms.documentid` ます。 ドキュメント ID を保持している場合は、ページビューやランキングなどのデータがターゲットアーティクルに転送されます。 これは、リダイレクトが主に名前の変更であり、同じコンテンツの一部のみをカバーする別の記事へのポインターではない場合に実行します。

リダイレクトを追加する場合は、古いファイルも必ず削除してください。

## <a name="creating-a-new-article"></a>新しい記事を作成しています

次のワークフローを使用して、web ブラウザーで GitHub を使用してドキュメントリポジトリに *新しい記事を作成* します。

1. Microsoft Docs/mixed reality の "マスター" ブランチからフォークを作成します (右上の [ **フォーク** ] ボタンを使用します)。

   ![Master ブランチをフォークします。](images/forkbranch.png)
2. "Mixed-reality" フォルダーで、右上にある [ **新しいファイルの作成** ] を選択します。
3. アーティクルのページ名を作成します (スペースの代わりにハイフンを使用し、句読点やアポストロフィは使用しません)。 "md" を追加します。

   ![新しいページの名前を指定します。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >必ず、"mixed-docs" フォルダー内から新しい記事を作成してください。 これを確認するには、新しいファイル名の行で "/mixed-reality-docs/" を確認します。

4. 新しいページの上部に、次のメタデータブロックを追加します。

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

5. [上記のセクション](#editing-an-existing-article)の手順に従って、関連するメタデータフィールドを入力します。
6. [Markdown の基礎](#markdown-basics)を使用して、記事の内容を記述します。
7. `## See also`記事の下部に、関連するその他の記事へのリンクが記載されたセクションを追加します。
8. 完了したら、[ **新しいファイルをコミット** する] を選択します。
9. [ **新しいプル要求** ] を選択し、フォークの ' master ' ブランチを microsoft docs/mixed reality ' マスター ' にマージします (矢印が正しい方法を指していることを確認します)。

   ![フォークからのプル要求を作成して、Microsoft Docs/mixed reality に](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown の基本

Markdown 言語を使用してドキュメントを編集する方法については、次のリソースを参照してください。

- [Markdown の基礎](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown リファレンスポスターの概要](images/MarkdownPoster.pdf)
- [Docs.microsoft.com の Markdown を作成するためのその他のリソース](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>テーブルの追加

Docs.microsoft.com スタイルの表では、インライン CSS を試す場合でも、罫線やカスタムスタイルはありません。 これは短時間は機能しているように見えますが、最終的には、プラットフォームによってテーブルからスタイルが除去されます。 そのため、事前に計画し、テーブルを単純にしておきます。 [Markdown テーブルを簡単に作成できるサイトは次のように](https://www.tablesgenerator.com/markdown_tables)なります。

[Visual Studio Code の Docs Markdown 拡張機能](https://docs.microsoft.com/teamblog/docs-extension)では、 [Visual Studio Code (下記参照)](#using-visual-studio-code)を使用してドキュメントを編集する場合にも、テーブルの生成を簡単に行うことができます。

### <a name="adding-images"></a>追加 (イメージを)

リポジトリの "mixed-reality/images" フォルダーにイメージをアップロードし、記事で適切に参照する必要があります。 画像は自動的にフルサイズで表示されます。これは、大きな画像が記事全体の幅を占めることを意味します。 イメージをアップロードする前に、イメージのサイズを事前に設定することをお勧めします。 推奨される幅は、600 ~ 700 ピクセルです。ただし、サイズの細かいスクリーンショットやスクリーンショットの一部である場合は、サイズを変更する必要があります。

>[!IMPORTANT]
>マージする前に、フォークされたリポジトリにのみイメージをアップロードできます。 そのため、記事にイメージを追加する予定がある場合は、まず、 [Visual Studio Code を使用](#using-visual-studio-code) して、最初にそのイメージをフォークの "images" フォルダーに追加するか、web ブラウザーで次の操作を行っていることを確認する必要があります。
>
>1. Microsoft Docs/mixed reality リポジトリをフォークしています。
>2. フォーク内のアーティクルを編集しています。
>3. 記事で参照しているイメージを、フォーク内の "mixed-reality/images" フォルダーにアップロードしました。
>4. フォークを Microsoft Docs/mixed reality の ' master ' ブランチにマージする **プル要求** を作成しました。
>
>独自にフォークしたリポジトリを設定する方法については、 [新しい記事を作成](#creating-a-new-article)するための手順に従ってください。

## <a name="previewing-your-work"></a>作業のプレビュー

Web ブラウザーを使用して GitHub で編集しているときに、ページの上部にある [ **プレビュー** ] タブを選択して、コミットする前に作業内容をプレビューすることができます。 

>[!NOTE]
>review.docs.microsoft.com での変更のプレビューは、Microsoft の従業員のみが利用できます。

Microsoft の従業員: 投稿物が ' master ' ブランチにマージされたら、コンテンツをで公開する前にレビューすることができ https://review.docs.microsoft.com/windows/mixed-reality?branch=master ます。 左側の列の目次を使用して、記事を探します。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>ブラウザーでの編集とデスクトップクライアントを使用した編集

クイック変更を行うには、ブラウザーでの編集が最も簡単な方法です。ただし、いくつかの欠点があります。

- スペルチェックは行われません。
- 他の記事へのスマートリンクは表示されません (記事のファイル名を手動で入力する必要があります)。
- イメージをアップロードして参照するのは面倒な場合があります。

これらの問題に対処しない場合は、貢献するときに、いくつかの[便利な拡張機能](#useful-extensions)を持つ[Visual Studio Code](https://code.visualstudio.com/)のようなデスクトップクライアントを使用します。

## <a name="using-visual-studio-code"></a>Visual Studio Code の使用

[上記](#editing-in-the-browser-vs-editing-with-a-desktop-client)の理由から、デスクトップクライアントを使用して、web ブラウザーではなくドキュメントを編集することをお勧めします。 [Visual Studio Code](https://code.visualstudio.com/)を使用することをお勧めします。

### <a name="setup"></a>セットアップ

このリポジトリを使用するように Visual Studio Code を構成するには、次の手順に従います。

1. Web ブラウザーで次のようにします。
    1. [PC の Git を](https://git-scm.com/downloads)インストールします。
    2. [Visual Studio Code](https://code.visualstudio.com/) をインストールします。
    3. まだお持ちでない場合は、 [Microsoft docs/mixed reality をフォーク](#creating-a-new-article)します。
    4. フォークで、[ **複製] または [ダウンロード** ] を選択し、URL をコピーします。
2. Visual Studio Code でフォークのローカル複製を作成します。
    1. [ **表示** ] メニューの [ **コマンドパレット**] をクリックします。
    2. 「Git: Clone」と入力します。
    3. コピーした URL を貼り付けます。
    4. コンピューターの複製を保存する場所を選択します。
    5. ポップアップで [ **リポジトリを開く** ] を選択します。

### <a name="editing-documentation"></a>ドキュメントの編集

次のワークフローを使用して、Visual Studio Code でドキュメントに変更を加えます。

>[!NOTE]
>Visual Studio Code を使用する場合は、記事の [編集](#editing-an-existing-article) と [作成](#creating-a-new-article) に関するすべてのガイダンスと、上記の [Markdown の編集の基礎](#markdown-basics)が適用されます。

1. 複製されたフォークが公式リポジトリを使用して最新の状態であることを確認します。
   1. Web ブラウザーでプル要求を作成して、Microsoft Docs/mixed reality ' master ' の他の共同作成者からの最近の変更をフォークに同期します (矢印が正しい方法であることを確認してください)。
      
      ![Microsoft Docs/mixed-reality からフォークへの変更の同期](images/sync_repos.PNG)
   2. Visual Studio Code で、[同期] ボタンを選択して、新しく更新されたフォークをローカルクローンに同期します。
      
      ![[同期] ボタンの画像をクリックします。](images/sync_clone.png)
2. Visual Studio Code を使用して、複製されたリポジトリのアーティクルを作成または編集します。
   1. 1つ以上の記事を編集します (必要に応じて、画像を "images" フォルダーに追加します)。
   2. 変更を **エクスプローラー** に **保存** します。
      
      ![エクスプローラーで [すべてを保存] を選択します。](images/explorer_save.png)
   3. **ソース管理** ですべての変更を **コミット** します (メッセージが表示されたら書き込みコミットメッセージ)。
      
      ![ソース管理で [すべてコミット] を選択する](images/source_control_commit.png)
   4. [ **同期** ] ボタンを選択して、変更内容を元に戻します (GitHub のフォーク)。
      
      ![[同期] ボタンをクリックします。](images/sync_back.png)
3. Web ブラウザーでプル要求を作成して、フォークの新しい変更を Microsoft Docs/mixed reality ' マスター ' に戻します (矢印が正しい方法であることを確認してください)。

   ![フォークからのプル要求を作成して、Microsoft Docs/mixed reality に](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>便利な拡張機能

ドキュメントを編集する際には、次の Visual Studio Code 拡張機能が役立ちます。

- [Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - **Alt + M キー** を使用して、次のような docs 作成オプションのメニューを表示します。
   - アップロードしたイメージを検索して参照します。
   - など、リスト、テーブル、ドキュメント固有の呼び出しなどの書式設定を追加 `>[!NOTE]` します。
   - 内部リンクとブックマーク (ページ内の特定のセクションへのリンク) を検索して参照します。
   - 書式設定エラーが強調表示されます (詳細については、エラーの上にマウスポインターを置きます)。
- [コードスペルチェッカー](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -スペルミスの単語に下線が引かれます。スペルミスの単語を右クリックして変更するか、辞書に保存します。
