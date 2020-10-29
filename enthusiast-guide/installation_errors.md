---
title: インストール エラー
description: Windows Mixed Reality の高度なインストールエラーのトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、インストール
appliesto:
- Windows 10
ms.openlocfilehash: 6837824346ce2390437daef0bc8eeab447f9e1f4
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686223"
---
# <a name="installation-errors"></a>インストール エラー

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"PC は Windows Mixed Reality を実行できません"

お使いの PC は、Windows Mixed Reality を実行するために必要な [最小要件](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) を満たしていません。 これは、コンピューターのハードウェアセットアップが Windows Mixed Reality と互換性がないか、 [最新バージョンの windows に更新](https://support.microsoft.com/en-us/help/12373/windows-update-faq)する必要があることが原因である可能性があります。 

Windows Mixed Reality では、少なくとも WDDM 2.2 をサポートするグラフィックスカードドライバーが必要であるため、製造元から最新のドライバー更新プログラムがインストールされていることを確認してください。 Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>「今のところ、この PC は Windows Mixed Reality を実行するために必要な最小要件を満たしていません」

お使いの PC は、Windows Mixed Reality の最良のエクスペリエンスを実現するために必要な [最小要件](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) を満たしていません。 お使いの PC では、イマーシブヘッドセットを実行できますが、特定のアプリケーションを実行できないか、パフォーマンスに問題がある可能性があります。

Windows Mixed Reality では、少なくとも WDDM 2.2 をサポートするグラフィックスカードドライバーが必要であるため、製造元から最新のドライバー更新プログラムがインストールされていることを確認してください。 Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Windows Mixed Reality をセットアップする前に、管理者が組織に対してこれを有効にする必要があります。 詳細情報

エンタープライズ管理ネットワークを使用していて、組織が Windows Server Update Services (WSUS) を使用しているか、ダウンロードをブロックする可能性のある他のポリシーを持っている可能性があります。 [Windows Mixed Reality を有効](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)にするには、組織の IT 部門またはシステム管理者に問い合わせてください。

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Mixed reality ソフトウェアをダウンロードできませんでした" または "ダウンロード中にハングしています"

* 保留中の更新によって、Mixed Reality ソフトウェアのダウンロードがブロックされることがあります。 [設定] にアクセスして **& セキュリティ > Windows Update を更新 >** 、Windows Update がオンになっていることを確認します。 次に、待機中の更新プログラムをダウンロードしてインストールします。 Windows Update エラーが発生した場合は、 [こちらで](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)ヘルプを表示してください。
* PC がインターネットに接続されており、少なくとも 2 GB の空き記憶領域があることを確認します。 ネットワークの状態を確認するには、[ **設定 > ネットワーク & インターネット > の状態** ] を確認します。 インターネットに接続できない場合は、 [こちら](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues)からヘルプを参照してください。  
* PC を再起動して、もう一度やり直してください。 

これらのソリューションが機能しない場合は、次のことを試してください。
* Wi-fi ネットワーク接続が [従量制課金](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq)に設定されている場合は、従量制課金に変更します。 従量制課金接続を無効にするには、[> 設定] [Network & Internet > > Status] の順に移動し、[ **従量制課金接続] として設定 > [接続プロパティの変更** ] を選択し、[オフ] を選択します。  
* 最近更新プログラムをインストールした場合は、問題が発生する可能性があります。 インストールされている更新プログラム、特に PC の安全を維持するセキュリティ更新プログラムを削除することはお勧めしませんが、最新の更新プログラムを削除すると、問題の原因を特定するのに役立つ場合があります。 これを行うには、次の手順を実行します。 
    * [ **設定] > 更新 & セキュリティ > インストールされている更新プログラムの表示 > 更新プログラムのアンインストール**
    * 最後にインストールした更新プログラムと [アンインストール] を選択します。
    * "この更新プログラムをアンインストールしますか?" というメッセージが表示されたら、 "Yes" と回答します。 これらの手順の実行中にエラーが発生した場合は、 [こちら](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)を参照してください。 
    * PC を再起動して、もう一度やり直してください。 
    * Windows Mixed Reality が正しくインストールされている場合は、[設定 > Windows Update の最新の更新プログラムを再インストールして **更新プログラムを確認 >** 、Windows mixed reality が引き続き動作しているかどうかを確認します。 正しくインストールされていない場合は、更新プログラムを再インストールして、Windows サポートに問い合わせてください。 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"問題が発生しました。 Windows Mixed Reality を開始できませんでした"
特定のエラーコードに関する詳細情報を取得するには、 [こちら](error-codes.md)を参照してください。 次のようにすることもできます。

* PC からヘッドセットケーブルを両方とも取り外します。
* PC を再起動します。
* [設定] にアクセスして **& セキュリティ > を更新 > Windows Update** 、Windows Update が有効になっていることを確認します。 待機中の更新プログラムをダウンロードしてインストールします。
* ヘッドセットを PC に再接続してから、セットアップを再試行してください。

これらの手順が機能しない場合は、Windows Mixed Reality をアンインストールしてから再インストールします。
* [設定] [ **Mixed reality > アンインストール** ] の > を選択し、[アンインストール] を選択します。 
* PC を再起動します。 
* もう一度セットアッププロセスを開始するには、ヘッドセットを PC に接続するだけです。
