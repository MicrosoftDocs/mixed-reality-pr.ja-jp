---
title: Mixed Reality ポータルのエラーメッセージ
description: Windows Mixed Reality の詳細なポータルメッセージのトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, 仮想現実, VR, MR, トラブルシューティング, エラー, ヘルプ, サポート, Mixed Reality ポータル
appliesto:
- Windows 10
ms.openlocfilehash: 11fa60b16a350d794a08db6a5f6120d88259c9ac
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685874"
---
# <a name="mixed-reality-portal-error-messages"></a>Mixed Reality ポータルのエラーメッセージ

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>"問題が発生しました" というエラーメッセージが表示されるか、または Mixed Reality ポータルで問題が発生しています。

Windows Mixed Reality を再起動します。
1. PC からヘッドセットケーブルの両方を切断します。
2. PC を再起動します。
3. ヘッドセットを再接続します。

それでもうまくいかない場合は、お使いの PC でヘッドセットが認識されていることを確認してください。
1. [スタート] を選択します。
2. 検索ボックスに「デバイスマネージャー」と入力し、一覧から選択します。 
3. [Mixed reality devices] を展開し、ヘッドセットが表示されているかどうかを確認します。 

一覧に表示されていない場合は、次の操作を試してください。
1. 使用可能な場合は、ヘッドセットを PC の別のポートに接続します。
2. Windows Update から、最新のソフトウェア更新プログラムを確認します。
3. Windows Mixed Reality をアンインストールして再インストールします。
    1. PC からヘッドセットケーブルの両方を切断します。
    2. [設定] を選択して **> Mixed reality > アンインストール** ] を選択します。
    3. [> 設定] を選択して、[ **Bluetooth & 他のデバイス >** デバイスをペアリングし、モーションコントローラーをします。 各コントローラーを選択し、[デバイスの削除] を選択します。
    4. ヘッドセットを PC に接続し直して、Windows Mixed Reality を再インストールします。
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>"USB ケーブルを確認してください" というエラーメッセージが表示できます。

ヘッドセットを別の USB ポートに接続します (SuperSpeed USB 3.0 であることを確認してください)。 また、ヘッドセットとコンピューターの間で extender またはハブを削除してみてください。

## <a name="im-getting-a-check-your-display-cable-error-message"></a>"ディスプレイケーブルを確認してください" というエラーメッセージが表示できます。

以下を試してみてください。
* ヘッドセットを DisplayPort 1.2 以降、または HDMI 1.4 以降に接続します。 ポートが PC の高度なグラフィックスカードと対応していることを確認します。
* アダプターを使用している場合は、4K 対応であることを確認してください。
* 別の HDMI ポートを使用してみてください。
* HDMI ポートに外付けモニターが接続されている場合は、代わりに DisplayPort に接続し、ヘッドセットの HDMI ポートを使用してください。
