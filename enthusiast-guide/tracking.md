---
title: Faq の追跡
description: Windows Mixed Reality の高度なトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、追跡
ms.openlocfilehash: b29df6f17bed52d3115faede10cdce91a7ea637f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685703"
---
# <a name="tracking-faqs"></a>Faq の追跡

## <a name="my-headset-has-stopped-tracking"></a>ヘッドセットの追跡が停止しました。

ライトが点灯していること、およびヘッドセットの前面に obstructing 追跡カメラが何もないことを確認します。 追跡が失われた場合、再開に数秒かかることがあります。 再開されない場合は、Windows Mixed Reality ポータルを再起動します。 

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>このように見えますが、変換できません (3D で行き詰まっています)。

これは、追跡システムがポーズを生成できないか、またはアプリケーションが新しいポーズデータを使用してレンダリングを停止したことを意味します。 次の点を確認します。
* 部屋に十分な光があることを確認します。
* トラックするのに十分な情報がルームにあることを確認します。
* デバイスを取り外し、Windows Mixed Reality を閉じて、デバイスにもう一度接続します。
* メッセージが引き続き表示される場合は、[カスタマーサポート](https://support.microsoft.com/)にお問い合わせください

## <a name="the-view-in-the-hmd-is-completely-frozen"></a>HMD のビューは完全に固定されています。

これは通常、アプリケーションまたはシステムレベルのコンポーネントで障害が発生したことを意味します。 試行する操作:
1. アプリケーションを終了するには、[ホーム] ボタンを押します。
2. デバイスを取り外し、MRP を閉じて、デバイスを再び接続します。
3. PC を再起動します。

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a>この世界では、通常に戻る前に、froze に傾いたり反転したりしています。

これは、アプリケーションまたはシステムレベルのコンポーネントによって致命的なエラーが発生したか、一時的にメモリまたは CPU リソースが不足していることが原因である可能性があります。 確認するには:
1. タスクマネージャーを開き、少なくとも20% の CPU が空いていることを確認し、400 MB のメモリが使用可能であり、ディスク IO が80% 未満になっていることを確認します。
2. **イベントビューアー > Windows ログ > アプリケーション** ] に移動して、凍結の時間の前後のエラーを探します。 HoloLens センサー、Mixed Reality、またはその時間内に実行されていたアプリケーションを指しているものを探します。 これらのログは、エラーの原因を説明する場合があります。
3. 問題が解決しない場合は、PC を再起動します。

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>少し反転して、通常の状態に戻ります。

これは通常、ヘッドセットからセンサーデータを取得して追跡アルゴリズムに通知するときのエラーが原因で発生します。 頻繁に発生する場合:
1. ヘッドセットを別の USB 3.0 ポートに接続します。
2. ヘッドホンを USB 3.0 ハブではなく PC に直接接続します。
3. 問題が解決しない場合は、 [カスタマーサポート](https://support.microsoft.com/)にお問い合わせください。

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>世界は傾いていますが、Windows Mixed Reality 内で移動したり、話したりすることができます。

センサーデータエラーが PC 上の環境データに記録された場合、Windows Mixed Reality が傾いている場合があります。 この問題を解決するには:
1. ヘッドセットを取り外し、Windows Mixed Reality を閉じて、ヘッドセットを再び接続します。
2. PC を再起動します。
3. 環境データをクリアします。

