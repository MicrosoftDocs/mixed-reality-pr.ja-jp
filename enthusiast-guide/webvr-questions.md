---
title: WebVR に関する Faq
description: Windows Mixed Reality の高度なトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、WebVR
ms.openlocfilehash: 8bc7ab010c1f6ebddf899262b09ba1d08f4ab3ae
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685623"
---
# <a name="webvr-faqs"></a>WebVR に関する Faq

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Edge から VR コンテンツを表示するときにコントローラーが表示できないのはなぜですか。

すべての WebVR コンテンツは、モーションコントローラーをサポートするために作成されるわけではありません。 WebVR を使用すると、コンテンツ開発者は、ゲームコントローラーやモーションコントローラーなど、さまざまな種類の入力をサポートできます。 サイトにコントローラーが表示されない場合は、モーションコントローラーがサポートされていない可能性があります。

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>イマーシブ WebVR ビューでマウスを使用できないのはなぜですか。

これは、WebVR 仕様のオプション機能です。 すべてのブラウザーがこの機能をサポートするわけではありません。また、マウス入力をサポートするためにすべての WebVR コンテンツが作成されるわけではありません WebVR を使用すると、コンテンツ開発者は、マウス、キーボード、ゲームコントローラー、またはモーションコントローラーなど、さまざまな種類の入力をサポートできます。 マウス入力の動作は、ブラウザーごとに異なります。 Microsoft Edge では、web サイトの作成者は、マウス入力が動作するためにヘッドセットに表示するときに "pointerlock ロック" を行う必要があります。

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>VR のエッジから、Youtube/Facebook/Vimeo/ガーディアンから360度のビデオを表示できないのはなぜですか。

Web サイトがブラウザーから直接 VR エクスペリエンスを起動できるようにする WebVR 仕様があります。この時点では、これらの web サイトの作成者がこの仕様を実装していません。 一部のプラットフォームでは、これらのベンダからの VR コンテンツの表示を可能にするアプリをダウンロードできます。

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Firefox または Chrome から VR を入力できないのはなぜですか。

WebVR は、現時点では Edge の Windows Mixed Reality デバイスでのみサポートされています。

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Web サイトから VR を入力したときに、ヘッドセットに空の画面が表示されるのはなぜですか。

Web サイトで、マルチ GPU マシン (ハイブリッド GPU ラップトップを含む) のサポートが実装されていない可能性があります。 試行する操作:
* ページを再度読み込みます。
* デスクトップコンピューターで、Microsoft Edge を表示しているモニターと同じグラフィックスアダプターにヘッドセットを接続します。 両方を高電力グラフィックスカードに接続し、統合されたグラフィックスアダプターには挿入しません。

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Edge からビデオを見ているときに VR を終了すると、サウンドは再生を続行しますが、エッジウィンドウはグレー表示されます。

これは、Mixed Reality 崖ハウスのエッジから WebVR を実行するときの既知の問題です。 これを解決するには、windows のボタンを押して WebVR エクスペリエンスを終了する代わりに、キーボードの esc キーを押すか、またはグレー表示のエッジウィンドウを選択してビデオを停止します。

## <a name="can-i-use-webvr-on-the-hololens"></a>HoloLens で WebVR を使用できますか。

この時点で、Microsoft は HoloLens での WebVR について何も発表していません。

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Edge から WebVR コンテンツを表示するときに、ビューが floor レベルで表示されるのはなぜですか。

この web サイトでは、Windows Mixed Reality ヘッドセットは正しくサポートされていません。 これを解決するには、次のようにします。
1. ヘッドセットをスペースの床に配置します。
2. (Mixed reality ではなく) デスクトップで Microsoft Edge を使用して WebVR ページに移動します。
3. [Enter VR] を選択します。
4. エクスペリエンスがイマーシブモードに完全に入るまで 5 ~ 10 秒待機します。
5. ヘッドセットに配置します。

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>一部の WebVR エクスペリエンスでは、表示が非常に低解像度です。

これらの web サイトは、高解像度ヘッドセットを正しくサポートしていません。 回避するには、次のようにします。
* (Mixed reality 崖家ではなく) デスクトップから WebVR を起動する場合は、[Enter VR] を選択する前にウィンドウが最大化されていることを確認します。
* VR を入力した後、Microsoft Edge ウィンドウのサイズを変更しないようにします。

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>ブラウザータブを変更すると WebVR イマーシブビューが終了するのはなぜですか。

これは正しい動作です。 セキュリティ上の理由から、接続されているヘッドセットにアクセスできるのは、[アクティブブラウザー] タブだけです。

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>特定の WebVR エクスペリエンスでオーディオを再生できないのはなぜですか。

Web サイトでは、Microsoft Edge で現在サポートされていない OGG オーディオファイル形式が使用されている可能性があります。

破損したサイトは、 [問題の追跡ツール](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)で Microsoft Edge ブラウザーチームに直接、または [#EdgeBug ハッシュタグ](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)を使用して twitter 経由で報告できます。

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Haptic のフィードバックが、motion controller と WebVR で動作しないのはなぜですか。

Microsoft Edge では、現在、WebVR ゲームパッド API 拡張機能の haptics はサポートされていません。

