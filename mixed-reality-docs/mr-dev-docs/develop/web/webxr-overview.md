---
title: Windows Mixed Reality での WebXR の使用
description: Windows Mixed Reality での WebXR の使用と開発の概要
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360 video、360ビデオ、360 photo、360 photos、360コンテンツ、イマーシブ web、immersiveweb、IW
ms.openlocfilehash: b72d4968e59e3e631138b1ecfd17ca9bbdd95c84
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416873"
---
# <a name="webxr-overview"></a>WebXR の概要

## <a name="what-is-webxr"></a>WebXR とは

**WebXR DEVICE API** は、 **Web** 上の **センサー** や **ヘッドマウントされたディスプレイ** など、 **仮想現実 (VR)** デバイスおよび拡張 **現実 (AR)** デバイスにアクセスするためのものです。 WebXR device API は現在 Microsoft Edge で使用でき、Chrome バージョン79以降では WebXR を既定としてサポートしています。 WebXR のブラウザーの最新のサポート状態は、 [caniuse.com](https://caniuse.com/#search=webxr)で確認できます。

[Windows Mixed Reality と新しい Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)の詳細については、「新[機能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)」セクションを参照してください。

## <a name="viewing-webxr"></a>WebXR の表示

> [!IMPORTANT]
> Microsoft Edge (レガシ) でサポートされるのは、現在のブラウザーでは使用できない非推奨の API である WebVR のみです。 ただし、新しい **[Chromium ベースの Edge ブラウザー](../../whats-new/new-microsoft-edge.md)** は WebXR をサポートしており、Windows Mixed REALITY の VR プロトタイプ作成に使用できます。 WebVR は、新しい Chromium ベースの Edge ブラウザーでは使用できません。
> 
> 現在、HoloLens 2 で WebXR をプロトタイプを作成する方法をお探しの場合は、 [Firefox の現実](https://mixedreality.mozilla.org/firefox-reality/)をご覧ください。

ブラウザーが WebXR をサポートしているかどうかをテストするには、ブラウザーで [WebXR サンプル](https://immersive-web.github.io/webxr-samples/) に移動します。

## <a name="see-also"></a>参照

* [WebXR Device API 仕様](https://immersive-web.github.io/webxr/)
* [WebXR Device API のドキュメント](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb](https://immersiveweb.dev/)
* [WebXR のサンプル](https://immersive-web.github.io/webxr-samples/)
* [Windows Mixed Reality と新しい Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [イマーシブ Web W3C Github](https://github.com/immersive-web)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) と [ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)
* [WebGL での失われたコンテキストの処理](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock ロック](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Babylon.js を使用した WebXR エクスペリエンスの作成](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [イマーシブ web コミュニティグループ](https://www.w3.org/community/immersive-web/)
