---
title: アプリの配布
description: サポートされているさまざまなプラットフォームおよび公開ストアのさまざまなディストリビューションオプションの概要です。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens、Mixed Reality、イマーシブヘッドセット、アプリ、uwp、送信、送信、フィルター、メタデータ、システム要件、キーワード、wack、認定、パッケージ、appx、販売促進
ms.openlocfilehash: 5c7a1d6e00610a4046bd71b07ca5184399c9e335
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925782"
---
# <a name="distributing-your-apps"></a>アプリの配布

![WMR ホームの Floaty 鳥3D アプリ lancher](images/distribute-hero-image.png)

アプリをユーザーの手に入れたり、世界に painstaking たりすることは、開発作業の中で最も重要で、場合によっては、その一部となることがあります。 以下に示す一連のリソースにプロセスを簡略化しました。これらはすべて、お客様またはチームに最適な配布とデプロイのシナリオによって異なります。

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>[分布] オプション

> [!IMPORTANT]
> * 別のパーティとアプリを共有している場合は、appx ファイルをビルドして提供する必要があります。 
>     * アプリインストーラーを使用している場合は、ユーザーと証明書を共有する必要もあります。
> 
> * 組織と共有している場合は、職場または学校のアカウントがあり、組織の [MDM (モバイルデバイス管理)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) インフラストラクチャにアクセスできる必要があります。  
>    * 共有パーティの場合は、テナントの管理者であり、 [Microsoft Endpoint Manager 管理センター](https://docs.microsoft.com/mem/intune/apps/apps-deploy) を使用してアプリを利用できるようにする必要があります。 別の方法として、appx ファイルとアプリの依存関係をエンドユーザーと共有することもできます。
>    * エンドユーザーの場合、アプリは、共有組織のテナントに登録すると、自動的にダウンロードされるか、ダウンロードできるようになります。 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>シナリオ</strong></td>
    <td><strong>ローカルデバイスのインストール</strong></td>
    <td><strong>だれとでも共有</strong></td>
    <td><strong>組織と共有する</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>アプリインストーラー</strong></a> ( <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider ビルド</a>を使用)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-ポータルサイト</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-必須アプリのインストール</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>ビジネス向け Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>プロビジョニングパッケージ</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#additional-scenarios"><strong>カスタム Win32 展開</strong></a> (HoloLens デバイスでは使用できません。下記を参照)</td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> アプリインストーラーは、現在、管理対象デバイスまたは HoloLens (第1世代) デバイスでは使用できません。

## <a name="additional-scenarios"></a>その他のシナリオ

* ストリームとゲームパスを含む Win32 アプリケーションのデプロイでは、Win32 を作成できます。Unity から PC スタンドアロンビルドターゲットを使用し、選択したプラットフォームに通常どおりにアプリを送信する EXE ファイル。 

* オフライン中に HoloLens 2 アプリケーションをインストールする必要がある場合は、オフラインの [Secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) の手順を参照するか、開発者モードを有効にせずにプロビジョニングパッケージを使用してアプリをインストールしてください。

* また、ビルドをデバイスに配置し、開発者モードが有効になっている他の開発者と共有することもできます。これには、 [Visual Studio でのデプロイとデバッグ](../develop/platform-capabilities-and-apis/using-visual-studio.md) 、または [デバイスポータルを使用したアプリケーションパッケージのインストール](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal)が含まれます。

## <a name="see-also"></a>関連項目
* [Microsoft Store からのアプリケーションの検索、インストール、およびアンインストール](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
