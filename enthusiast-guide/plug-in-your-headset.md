---
title: ヘッドセットを接続する
description: Windows Mixed Reality ヘッドセットを USB 3.0、HDMI、ヘッドホンに接続する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、ヘッドセット、セットアップ、はじめに
appliesto:
- Windows 10
ms.openlocfilehash: d68c56813c65325d9cab24488f6676d41da435a2
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725993"
---
# <a name="plug-in-your-headset"></a>ヘッドセットを接続する

## <a name="connect-your-headset-to-your-pcs-usb-30-port"></a>ヘッドセットを PC の USB 3.0 ポートに接続する

コンピューターの USB 3.0 ポートを特定し、USB ケーブルを接続します。 USB 3.0 ポートには、その横に SS (超 Speed) が書き込まれています。 多くの場合、blue ですが、常にではありません。

PC 上に十分な空き USB ポートがない場合は、AC 電源を使用した [外付け usb 3.0 ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)を使用できます。

## <a name="connect-your-headset-to-your-pcs-hdmi-out-port"></a>ヘッドセットを PC の HDMI 出力ポートに接続する

コンピューターの HDMI 出力ポートを特定し、ヘッドセットの HDMI ケーブルを接続します。 ポートで HDMI に接続してい **ない** ことを確認します。

## <a name="connect-headphones-to-your-headset"></a>ヘッドホンをヘッドセットに接続する

統合された AKG ヘッドホンとデュアルアレイマイク (Samsung HMD Odyssey ヘッドセット、HP リバーブ、HP リバーブ G2 など) を使用してデバイスを購入した場合を除き、3.5-mm オーディオジャックのヘッドホンが必要になります。

## <a name="common-issues"></a>一般的な問題

* USB 3.0 ケーブルを差し込む前に、HDMI ケーブルを接続しています。  HDMI ケーブルを接続する **前に** 、USB 3.0 ケーブルを接続していることを確認します。
* HMD の USB ケーブルの横にある bluetooth アダプターに接続している。 Bluetooth アダプターの横にヘッドセットの USB ケーブルを接続し **ない** でください。これは、結果として得られる無線干渉が bluetooth のパフォーマンスに悪影響を及ぼす可能性があるためです。
* 両方がある Pc の dGPU HDMI ポートではなく、iGPU HDMI ポートに HDMI ケーブルを接続しました。 一部のデスクトップ Pc には、統合グラフィックスプロセッシングユニット (iGPU) と離散グラフィックスプロセッシングユニット (dGPU) の両方があります。 iGPU ポートは、多くの場合、無効になっています。 PC に dGPU が搭載されている場合は、ヘッドセットを dGPU に接続する必要があります。  
* PC に HDMI ポートがない場合は、アダプターが必要になることがあります。 [推奨されるアダプターの完全な一覧については、こちらを参照して](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)ください。
* ヘッドセットを Surface デバイスに接続しています。 「 [Windows Mixed Reality で Surface を使用する」を](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)参照してください。

## <a name="see-also"></a>関連項目

* [ヘッドセット接続のトラブルシューティング](headset-connectivity.md)
* [Windows Mixed Reality をインストールする](install-windows-mixed-reality.md)
* [推奨されるアダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* [最小 PC ハードウェア ガイドライン](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
