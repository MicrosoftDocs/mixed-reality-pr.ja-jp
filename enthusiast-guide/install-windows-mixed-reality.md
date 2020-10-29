---
title: Windows Mixed Reality ソフトウェアのインストール
description: Windows Mixed reality ヘッドセットにプラグインした後、Mixed Reality ポータルアプリを使用して、Windows Mixed Reality 機能を開始およびダウンロードします。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、はじめに、セットアップ、Mixed Reality ポータル
appliesto:
- Windows 10
ms.openlocfilehash: 5e04f29f834b2220f51f1748aa59e4188d8ad38d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686530"
---
# <a name="install-windows-mixed-reality-software"></a>Windows Mixed Reality ソフトウェアのインストール

## <a name="launch-mixed-reality-portal"></a>Mixed Reality ポータルを起動する

Windows Mixed Reality ヘッドセットをプラグインし、ドライバーが正常にインストールされると、混合 Reality ポータル (MRP) がデスクトップで自動的に起動します。 これが自動的に行われない場合は、いつでも [スタート] メニュー ([ **> Mixed Reality ポータルの開始** ]) から mixed reality ポータルを起動することができます。 ポータルが起動したら、[ **開始** ] をクリックします。

![Mixed Reality へようこそ](images/1050px-mixedrealityportal.png)

Mixed Reality ポータルでは、次のことができます。

* ヘッドセットにビューのライブストリームを表示します (Windows Mixed Reality ウルトラのみ)。 これをオンまたはオフにするには、[プレビューの停止] または [プレビューの開始] を選択します。 (Mixed reality の [スタート] メニューからプレビューをオンまたはオフにすることもできます)。
* ヘッドセットとコントローラーの状態を確認します。 すべての情報を表示するには、[メニュー] を選択します。
* 新しいコントローラーを設定します。 [メニュー] を選択し **> コントローラーを設定** します。
* 境界をオンまたはオフにします。 [ **メニュー > 境界のオン/オフ]** を選択します。 (オフにすると、安全性を確保するために1つの場所に置く必要があります)。
* 新しい境界を作成します。 [メニュー] を選択し **> セットアップを実行** します。
* Mixed reality の写真にアクセスします。 **メニュー > [mixed reality の写真** ] を選択します。
* Mixed reality アプリとゲームを取得します。 [メニュー] を選択し、 **mixed reality アプリ > 取得** します。

## <a name="download-windows-mixed-reality"></a>Windows Mixed Reality のダウンロード

Windows Mixed Reality のサイズは約 1 GB です。ダウンロードにかかる時間は、インターネット接続によって異なります。 "Mixed Reality ソフトウェアをダウンロードできませんでした" というメッセージが表示された場合は、 [トラブルシューティングの手順](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading)を確認してください。

## <a name="general-troubleshooting"></a>一般的なトラブルシューティング

混合 Reality ポータルを使用しているときに問題が発生したりエラーメッセージが表示されたりする場合は、次のソリューションを試してください。

**Windows Mixed Reality の再起動**

1. ヘッドセットを PC から切断します (両方のケーブル)。
2. PC を再起動し、ヘッドセットを再接続します。

**PC でヘッドセットが認識されていることを確認する**

再起動がうまくいかない場合は、ヘッドセットが PC で認識されていることを確認してください。 [スタート] を選択し、検索ボックスに「device manager」と入力して、一覧から選択します。 [Mixed reality デバイス] を展開し、ヘッドセットが表示されているかどうかを確認します。 

一覧に表示されていない場合は、次の操作を試してください。
* 使用可能な場合は、ヘッドセットを PC の別のポートに接続します。
* [Windows Update](https://support.microsoft.com/help/12373)から、最新のソフトウェア更新プログラムを確認します。
* Windows Mixed Reality をアンインストールして再インストールします。
    1. ヘッドセットを PC から切断します (両方のケーブル)。
    2. [設定] を選択して **> Mixed reality > アンインストール** ] を選択します。
    3. モーションコントローラーをペアリングする: [ **設定] > [Bluetooth & 他のデバイス > デバイス** ] を選択します。 各コントローラーを選択し、[ **デバイスの削除** ] を選択します。
    4. Windows Mixed Reality を再インストールするには、ヘッドセットを PC に接続し直します。

## <a name="common-error-messages"></a>一般的なエラー メッセージ

ここでは、表示される可能性のある [エラーメッセージ](error-codes.md) について説明します。

| このメッセージが表示する場合 | 次の操作を試してみてください |
| --- | --- |
| USB ケーブルを確認する | ヘッドセットを別の USB ポートに接続します (SuperSpeed USB 3.0 であることを確認してください)。 また、ヘッドセットとコンピューターの間で extender またはハブを削除してみてください。 |
| ディスプレイケーブルを確認する | 以下を試してみてください。 <ul><li>ヘッドセットを DisplayPort 1.2 以降、または HDMI 1.4 以降に接続します。 ポートが PC の高度なグラフィックスカードと対応していることを確認します。</li><li>アダプターを使用している場合は、4K 対応であることを確認します。</li><li>別の HDMI ポートを使用してみてください</li><li>HDMI ポートに外付けモニターが接続されている場合は、代わりに DisplayPort に接続してみてください。ヘッドセットには HDMI ポートを使用してください。</li></ul> |
| 問題が発生した場合 | 上記の一般的なトラブルシューティング手順に従います。 |

## <a name="review-and-accept-terms-and-conditions"></a>使用条件を確認して同意する

セットアップを続行するには、PC に 2 GB の空き領域が必要です。 続行するには、[使用条件に **同意** します] をクリックします

![使用条件に同意する](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>互換性チェック

次は、互換性のあるチェックです。 Mixed Reality ポータルでは、お使いの PC が mixed reality と互換性があることを確認します。 **緑色** のチェックは、必要な項目が PC から渡されたことを意味します。 **オレンジ色** の三角形は、特定の要件に対して PC に問題がある可能性があることを意味します。 問題が発生した場合は、トラブルシューティングまたは PC のアップグレードが必要になることがあります。 **赤** X は、指定された項目の要件を PC が満たしていないことを意味します。

![互換性チェック](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>開発の準備

スピンアイコンを使用して、画面に "セットアップの準備ができました" というメッセージが表示されます。 これには少し時間がかかります。

![セットアップの準備をしています](images/1050px-gettingsetup.png)

## <a name="see-also"></a>関連項目
* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [インストールのトラブルシューティング](installation_errors.md)
* [セットアップのトラブルシューティング](set-up-questions.md)
* [Windows Mixed Reality のセットアップ](set-up-windows-mixed-reality.md)
