---
title: WebVR に関する Faq
description: 標準的なコンシューマーサポートドキュメントを超えている web アプリケーションについては、Mixed Reality のトラブルシューティングを使用して最新情報を入手してください。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、WebVR
ms.openlocfilehash: dc7a0b28e19f4f1fc029489aae2ea375e43b8d3b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008662"
---
# <a name="webvr-faqs"></a>WebVR に関する Faq

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Edge から VR コンテンツを表示するときにコントローラーが表示できないのはなぜですか

すべての WebVR コンテンツは、モーションコントローラーをサポートするために作成されるわけではありません。 WebVR を使用すると、コンテンツ開発者は、ゲームコントローラーやモーションコントローラーなど、さまざまな種類の入力をサポートできます。 サイトにコントローラーが表示されない場合は、モーションコントローラーがサポートされていない可能性があります。

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>イマーシブ WebVR ビューでマウスを使用できないのはなぜですか。

マウスの使用は、WebVR 仕様のオプション機能です。 すべてのブラウザーがこの機能をサポートするわけではありません。また、マウス入力をサポートするためにすべての WebVR コンテンツが作成されるわけではありません WebVR を使用すると、コンテンツ開発者は、マウス、キーボード、ゲームコントローラー、またはモーションコントローラーなど、さまざまな種類の入力をサポートできます。 マウス入力の動作は、ブラウザーごとに異なります。 Microsoft Edge では、web サイトの作成者は、マウス入力が動作するためにヘッドセットに表示するときに "pointerlock ロック" を行う必要があります。

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>VR のエッジから、Youtube/Facebook/Vimeo/ガーディアンから360度のビデオを表示できないのはなぜですか。

Web サイトがブラウザーから直接 VR エクスペリエンスを起動できるようにする WebVR 仕様があります。 これらの web サイトの作成者は、現時点でこの仕様を実装していません。 一部のプラットフォームでは、これらのベンダからの VR コンテンツの表示を可能にするアプリをダウンロードできます。

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Firefox または Chrome から VR を入力できないのはなぜですか。

WebVR は、現時点では Edge の Windows Mixed Reality デバイスでのみサポートされています。

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Web サイトから VR を入力したときに、ヘッドセットに空の画面が表示されるのはなぜですか。

Web サイトで、マルチ GPU マシン (ハイブリッド GPU ラップトップを含む) のサポートが実装されていない可能性があります。 試行する操作:

* ページを再度読み込みます。
* デスクトップコンピューターで、Microsoft Edge を表示しているモニターと同じグラフィックスアダプターにヘッドセットを接続します。 両方を高電力グラフィックスカードに接続し、統合されたグラフィックスアダプターには挿入しません。

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Edge からビデオを見ているときに VR を終了すると、サウンドは再生を続行しますが、エッジウィンドウはグレー表示されます。

これは、Mixed Reality 崖ハウスのエッジから WebVR を実行するときの既知の問題です。 これを解決するには、windows のボタンの代わりに、キーボードの esc キーを押して WebVR エクスペリエンスを終了するか、グレー表示のエッジウィンドウを選択してビデオを停止します。

## <a name="can-i-use-webvr-on-the-hololens"></a>HoloLens で WebVR を使用できます

この時点で、Microsoft は HoloLens での WebVR について何も発表していません。

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Edge から WebVR コンテンツを表示するときに、ビューが floor レベルで表示される理由

Web サイトは、Windows Mixed Reality ヘッドセットを正しくサポートしていません。 これを解決するには、次のようにします。

1. ヘッドセットをスペースの床に配置します。
2. (Mixed reality ではなく) デスクトップで Microsoft Edge を使用して WebVR ページに移動します。
3. [Enter VR] を選択します。
4. エクスペリエンスがイマーシブモードに完全に入るまで 5 ~ 10 秒待機します。
5. ヘッドセットに配置します。

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>一部の WebVR エクスペリエンスでは、表示が低解像度になります。

これらの web サイトは、高解像度のヘッドセットを正しくサポートしていません。 これを解決するには、次のようにします。

* (Mixed reality 崖家ではなく) デスクトップから WebVR を起動する場合は、[Enter VR] を選択する前にウィンドウが最大化されていることを確認します。
* VR を入力した後、Microsoft Edge ウィンドウのサイズを変更しないようにします。

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>ブラウザータブを変更すると WebVR イマーシブビューが終了するのはなぜですか

これは通常の動作です。 セキュリティ上の理由から、接続されているヘッドセットにアクセスできるのは、[アクティブブラウザー] タブだけです。

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>特定の WebVR エクスペリエンスでオーディオを再生できないのはなぜですか。

Web サイトは、Microsoft Edge で現在サポートされていない OGG オーディオファイル形式を使用している可能性があります。

破損したサイトは、 [問題の追跡ツール](https://developer.microsoft.com/microsoft-edge/platform/issues/)で Microsoft Edge ブラウザーチームに直接、または [#EdgeBug ハッシュタグ](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)を使用して twitter 経由で報告できます。

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Haptic フィードバックが WebVR とモーションコントローラーで動作しないのはなぜですか。

Microsoft Edge では、現在、WebVR ゲームパッド API 拡張機能の haptics はサポートされていません。