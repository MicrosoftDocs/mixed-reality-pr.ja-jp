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
ms.openlocfilehash: 78f1a66ea6e853e55b8020747abea22a1dc686e5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684442"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Mixed Reality 愛好ガイドへの貢献

このガイドに関心をお寄せいただき、ありがとうございます。 お客様からのフィードバック、編集、追加、ドキュメントの改善にご協力いただき、ありがとうございます。このページでは、貢献するための基本的な手順とガイドラインについて説明します。

> [!IMPORTANT]
> docs.microsoft.com に公開されるすべてのリポジトリには、「[Microsoft Open Source Code of Conduct (Microsoft オープンソース倫理規定)](https://opensource.microsoft.com/codeofconduct/)」が適用されています。 詳細については、[倫理規定についてのよくある質問](https://opensource.microsoft.com/codeofconduct/faq/)に関するページをご覧いただくか、[opencode@microsoft.com](mailto:opencode@microsoft.com) 宛てに質問またはコメントを送信してください。<br>
>
> パブリック リポジトリにあるドキュメントおよびコード例に対する軽微な修正や明確化は、「[docs.microsoft.com - 使用条件](https://docs.microsoft.com/legal/termsofuse)」の対象になります。 Microsoft の従業員ではない共同作成者が新規または大幅な変更を行うと、オンライン貢献者使用許諾契約書 (CLA) の提出をお願いするコメントが pull request 内に生成されます。 pull request が正しく受理されるように、オンライン フォームへのご記入をお願いいたします。

## <a name="how-to-make-a-change"></a>変更する方法

| ドキュメントへの変更を提案するには、次の手順に従ってください。 | Screenshots (スクリーンショット) |
| :------------------- | :--------: |
| 1. Docs.microsoft.com ページを表示している場合は、ページの右上にある [ **編集** ] ボタンをクリックします。  [GitHub リポジトリ](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)内の対応するマークダウン ソース ファイルにリダイレクトされます。 | ![[編集] ボタン](images/edit_button.jpg) |
| 2. まだ GitHub アカウントを持っていない場合は、右上にある [ **サインアップ** ] をクリックして新しいアカウントを作成します。 | ![サインアップボタン](images/signup-for-github-button.png)|
| 3. 対応する GitHub ページが開いたら、[編集] (鉛筆アイコン) をクリックします。 | ![鉛筆ボタン](images/pencil_button.jpg)|
| 4. [ファイルの編集] ウィンドウで、Markdown language を使用してコンテンツを変更します。 ([Markdown を記述する方法](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![ファイルの編集](images/edit-in-github.png)|
| 5. [変更のプレビュー] をクリックして、書式設定が想定どおりに表示されることを確認します。 | ![変更のプレビュー](images/edit-in-github.png)|
| 6. 完了したら、ページの一番下までスクロールし、[ファイルの変更の提案] をクリックすると、[変更の比較] ページが表示され、変更を確認できます。 次に、[プル要求の作成] ボタンをクリックして、変更を送信します。 これで完了です。 | ![変更を提案する](images/propose.jpg)|

(プル要求を使用して) 変更を送信した後は、ドキュメントチームのメンバーによってレビューされます。 要求が受け入れられた場合、更新プログラムはに発行され [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) ます。

* 内部レビューのみの場合は、で変更を確認でき [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) ます。

## <a name="working-with-branches"></a>ブランチを操作する

2つの主要な親分岐 ([マスター](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)) を使用するのは、 [Mixed Reality のガイド GitHub リポジトリ](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)です。このコンテンツ[は、](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)[ライブサイト](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)で表示されるコンテンツの[ステージングサイト](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)で確認できます。

投稿を作成するときは、プル要求 (PR) を **Master** ブランチに送信してください。 このブランチはステージング サイトで表示でき、ライブで公開する準備ができている投稿のみを含んでいます。 また、独自の一意のブランチ名を使用してブランチを作成し、送信することもできます。これは、ステージングサイトで選択して表示できます。 ( **ライブ** ブランチは、コンテンツ管理者のみが使用できます)。

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Windows Mixed Reality 愛好ガイドに関するフィードバックを提供するための問題の使用

フィードバックを提供したり、問題を指摘したりするには、実際のドキュメントページを直接変更するのではなく、問題を [作成](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) します。コンテンツの所有者は、問題を適切なタイミングで解決するのに最適です。

特定のページに関する問題を作成する場合は、トピックタイトルと URL を必ず含めてください。

このコンテンツをサポートしていただき、ありがとうございます。
