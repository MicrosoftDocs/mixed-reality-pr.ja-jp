---
title: ヘッドセットを接続する
description: Windows Mixed Reality ヘッドセットを USB 3.0 および HDMI に接続する方法と、ヘッドホンをヘッドセットに接続する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、ヘッドセット、セットアップ、はじめに
appliesto:
- Windows 10
ms.openlocfilehash: 46b40a09c88013515911026cbd03a6fc6d19e1ca
ms.sourcegitcommit: 2cdc2e38990fff24972d98f9e74f0dabacbffa7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92153507"
---
# <a name="plug-in-your-headset"></a>ヘッドセットを接続する

## <a name="connect-your-headset-to-your-pcs-usb-30-port"></a>ヘッドセットを PC の USB 3.0 ポートに接続する

コンピューターの USB 3.0 ポートを特定し、USB ケーブルを接続します。 USB 3.0 ポートには、その横に SS (超 Speed) が書き込まれています。 多くの場合、青になります (常にではありません)。

PC に十分な数の USB ポートがない場合は、 [AC 電源の外部 USB 3.0 ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)を使用できます。

## <a name="connect-your-headset-to-your-pcs-hdmi-out-port"></a>ヘッドセットを PC の HDMI 出力ポートに接続する

コンピューターの HDMI 出力ポートを特定し、ヘッドセットの HDMI ケーブルを接続します。 ポートの HDMI に接続して **いない** ことを確認します。

## <a name="connect-headphones-to-your-headset"></a>ヘッドホンをヘッドセットに接続する

Samsung HMD Odyssey ヘッドセット、HP リバーブ、または HP リバーブ G2 (AKG ヘッドホンと統合デュアルアレイマイクが統合されている) を購入していない場合は、ヘッドセットの 3.5 mm オーディオジャックに接続できるヘッドホン (可能であればインラインマイクを使用) に接続する必要があります。

## <a name="common-issues"></a>一般的な問題
* USB 3.0 ケーブルを差し込む前に、HDMI ケーブルを接続しています。  HDMI ケーブルを接続する **前に** 、USB 3.0 ケーブルを接続していることを確認します。
* HMD の USB ケーブルの横にある bluetooth アダプターに接続している。  Bluetooth アダプターを使用している場合は、そのアダプターの横にヘッドセットの USB ケーブルを接続し **ないでください。これ** により、無線干渉が bluetooth のパフォーマンスに悪影響を及ぼす可能性があります。
* DGPU hdmi ポートの代わりに、HDMI ケーブルを iGPU HDMI ポートに接続しています (両方がある Pc の場合)。 一部のデスクトップ Pc には、統合グラフィックスプロセッシングユニット (iGPU) と離散グラフィックスプロセッシングユニット (dGPU) の両方があり、多くの場合、iGPU ポートは無効になっています。 PC に dGPU が搭載されている場合は、ヘッドセットを dGPU に接続する必要があります。  
* PC に HDMI ポートがない場合は、アダプターが必要になることがあります。 [推奨されるアダプターの完全な一覧については、こちらを参照して](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)ください。 
* ヘッドセットを Surface デバイスに接続しています。 「 [Windows Mixed Reality で Surface を使用する」を](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)参照してください。

## <a name="see-also"></a>関連項目

* [ヘッドセット接続のトラブルシューティング](headset-connectivity.md)
* [Windows Mixed Reality をインストールする](install-windows-mixed-reality.md)
* [推奨されるアダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* [最小 PC ハードウェア ガイドライン](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
