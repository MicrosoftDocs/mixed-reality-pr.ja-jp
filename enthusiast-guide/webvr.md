---
title: Windows Mixed Reality での WebVR の使用
description: WebVR の基本、Windows Mixed Reality ヘッドセットで Microsoft Edge と共に使用する方法、および一般的なトラブルシューティングの問題について説明します。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、WebVR、Edge、Microsoft Edge、web 閲覧
ms.openlocfilehash: 0b0d07383b43feaa11fb9bfac2b071d8d4d80b19
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009442"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Windows Mixed Reality での WebVR の使用

>[!IMPORTANT]
>ほとんどの最新の web ブラウザーでは、WebXR を優先して非推奨の WebVR サポートを使用しています。これは、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準です。 [新しい Microsoft Edge](using-microsoft-edge.md) for WebXR サポートをインストールしてください。

## <a name="what-is-webvr"></a>WebVR とは

[Webvr](https://webvr.info) は、ブラウザーからの VR 権限を体験できるオープンな仕様です。 Web サイトが WebVR サポートを実装し、3D コンテンツを提供する場合、ユーザーの同意と共に、ヘッドホンにイマーシブコンテンツを表示できます。

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Webhook での WebVR と web の閲覧の違い

WebVR は、web サイトの作成者が VR 機能をページに追加できるようにするテクノロジです。 WebVR API は、ヘッドセット全体に3D コンテンツ (360 度のビデオ、3D モデル、3d ゲームなど) を表示するためにページによって使用されます。 **例:**[Cnn.com/vr](http://cnn.com/vr)での360ビデオの表示。 ページが WebVR をサポートしている場合は、[] ボタンまたはその他の UI 要素を追加して、VR と入力することができます。

VR で web を閲覧することは、プラグインを装着するときに Edge ブラウザーを使用することを意味します。これは、Cliffhouse 内の2D アプリスレートです。

## <a name="do-all-websites-support-webvr"></a>すべての web サイトが WebVR をサポートする

いいえ。 Web サイトの作成者は、WebVR を使用することを選択する必要があります。また、特定のブラウザー、ヘッドセット、およびコントローラー用に最適化されたサイトを作成できます。 一部の WebVR コンテンツは、mobile VR デバイスに対してのみ最適化されています。 また、web サイトでは、WebVR コンテンツを明示的に作成して提供する必要があることに注意してください。 WebVR と互換性のあるいくつかのコンテンツがあるサイトの数が毎日増加しています。

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Naopak/Oculus などを使用して Microsoft Edge の WebVR コンテンツを表示できますか。

いいえ。 エッジで WebVR を使用するには、Windows Mixed Reality ヘッドセットが必要です。 ただし、別のブラウザーで WebVR コンテンツにアクセスすることはできます。互換性のあるデバイスとブラウザーの完全な一覧については、「 [Webvr. 岩](http://webvr.rocks/)」を参照してください。

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>WebVR 開発者向けドキュメントはどこで入手できますか。

開発者向けドキュメントについては、「 [Webvr Developer documentation](https://docs.microsoft.com/microsoft-edge/webvr/)」を参照してください。

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>Windows Mixed Reality では動作しない WebVR を使用した web サイトが見つかりました。 どうしようか

破損したサイトは、 [問題の追跡ツール](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)で Microsoft Edge ブラウザーチームに直接、または [#EdgeBug ハッシュタグ](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)を使用して twitter 経由で報告できます。

カテゴリの下にある Windows フィードバックハブアプリを使用して、バグをログに記録することもできます。

Microsoft Edge > Web サイトの問題

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>WebVR が動作しているかどうかをテストするための適切なページ

[Webvr.info のサンプル](http://webvr.info/samples/XX-vr-controllers.html)を参照してください。

## <a name="how-do-i-set-up-webvr"></a>WebVR をセットアップ操作方法には

Windows Mixed Reality ヘッドセット (ハードウェアまたはシミュレーションを使用) で WebVR コンテンツを体験するには、次の操作を行う必要があります。

1. ヘッドセットが接続されていることを確認します。
2. デスクトップまたは Mixed Reality のいずれかで Microsoft Edge を起動します。
3. WebVR enabled ページに移動します。
4. ページ内の Enter キーを押します (このボタンの場所と視覚的な表現は、web サイトごとに異なる場合があります)。 次のようになります。 \
   ![VR メガネイメージ](images/75px-enter-vr.png)
5. 特定のドメインに対して最初に VR を入力しようとすると、ブラウザーはイマーシブビューの使用に同意するように要求し、[はい] を選択します。 ![特定のドメインに対して最初に VR を入力しようとしたときに表示される同意 UI](images/1053px-Webvr-consent-ui.png)
6. ヘッドセットで WebVR コンテンツの表示が開始されます。

## <a name="see-also"></a>関連項目

* [WebVR > のトラブルシューティング](webvr-questions.md)
* [初めての WebVR エクスペリエンスを利用する方法](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [Windows Mixed Reality でのゲームとアプリの使用](using-games-and-apps-in-windows-mixed-reality.md)
* [Mixed Reality ホーム](your-mixed-reality-home.md)
* [追跡システム](tracking-system.md)
* [モーションコントローラー](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [フィードバックの提出](filing-feedback.md)
