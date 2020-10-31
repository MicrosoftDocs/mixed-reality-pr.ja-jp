---
title: Windows Mixed Reality での WebVR の使用
description: WebVR について説明します。また、Windows Mixed Reality ヘッドセットで Microsoft Edge と共に使用する方法についても説明します。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、WebVR、Edge、Microsoft Edge、web 閲覧
ms.openlocfilehash: 8e8d7b5feefe5b1eccad0684808b40b63e9bbbca
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131856"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>Windows Mixed Reality での WebVR の使用

>[!IMPORTANT]
>ほとんどの最新の web ブラウザーでは、WebXR を優先して非推奨の WebVR サポートを使用しています。これは、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準です。 [新しい Microsoft Edge](using-microsoft-edge.md) for WebXR サポートをインストールしてください。

## <a name="what-is-webvr"></a>WebVR とは

[Webvr](https://webvr.info) は、ブラウザーで VR を体験できるようにするオープンな仕様です。 Web サイトが WebVR サポートを実装し、3D コンテンツを提供する場合、ユーザーの同意と共に、ヘッドホンにイマーシブコンテンツを表示できます。

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>Webhook での WebVR と web の閲覧の違い

WebVR は、web サイトの作成者が VR 機能をページに追加できるようにするテクノロジです。 WebVR API は、ヘッドセット全体に3D コンテンツ (360 度のビデオ、3D モデル、3d ゲームなど) を表示するためにページによって使用されます。 **例:**[Cnn.com/vr](http://cnn.com/vr)での360ビデオの表示。 ページが WebVR をサポートしている場合は、ボタンまたはその他の UI 要素が追加され、これをクリックして VR を入力することができます。

VR で web を閲覧することは、プラグインを装着している間に、microsoft Edge ブラウザーを使用することを意味します。これは、Cliffhouse 内の2D アプリスレートです。

## <a name="do-all-websites-support-webvr"></a>すべての web サイトが WebVR をサポートする

不正解です。 Web サイトの作成者は、WebVR を使用することをオプトインする必要があります。さらに、特定のブラウザー、ヘッドセット、およびコントローラー用に最適化されたサイトを作成することもできます。 たとえば、一部の WebVR コンテンツは mobile VR デバイスに対してのみ最適化されています。 また、web サイトでは、WebVR コンテンツを明示的に作成して提供する必要があることに注意してください。 WebVR と互換性のあるいくつかのコンテンツがあるサイトの数が毎日増加しています。

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>Naopak/Oculus などを使用して Microsoft Edge の WebVR コンテンツを表示できますか。

不正解です。 Windows Mixed Reality ヘッドセットを使用して、エッジで WebVR を使用する必要があります。 ただし、別のブラウザーで WebVR コンテンツにアクセスできる場合があります。互換性のあるデバイスとブラウザーの完全な一覧については、「 [Webvr. 岩](http://webvr.rocks/)」を参照してください。

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
4. ページ内の Enter VR ボタンをクリックします (このボタンの位置と表示は、web サイトごとに異なる場合があります)。 次のようになります。 \
   ![VR メガネイメージ](images/75px-enter-vr.png)
5. 特定のドメインに対して最初に VR を入力しようとすると、ブラウザーはイマーシブビューの使用に同意するように要求し、[はい] をクリックします。 ![特定のドメインに対して最初に VR を入力しようとしたときに表示される同意 UI](images/1053px-Webvr-consent-ui.png)
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
