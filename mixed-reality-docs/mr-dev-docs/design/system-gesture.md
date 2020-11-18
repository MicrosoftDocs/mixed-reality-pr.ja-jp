---
title: 開始ジェスチャ
description: スタートメニューを呼び出す開始ジェスチャ。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed reality、ジェスチャ、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ブルーム
ms.openlocfilehash: 1994b38341dfdb2ef1cdb326cf7747c0af5f9c34
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703268"
---
# <a name="start-gesture"></a>開始ジェスチャ

Start ジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。 これは、キーボードの Windows キー、Xbox コントローラーの Xbox ボタン、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。 相互作用を設計するときの競合を防ぐため、各 Mixed Reality デバイスでシステム用に予約されているジェスチャを理解することが重要です。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>Bloom (ブルーム)</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>手首ボタン</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>視線とパームアップのピンチ</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom (ブルーム)
HoloLens (第1世代) の [スタート] メニューを表示するには、"ブルーム" を設計しました。これは、花開花を模倣したシンボリックジェスチャです。 これは、簡単に操作できるようにするためのものであり、簡単に実行でき、簡単に再現できます。 HoloLens (第1世代) でブルームジェスチャを実行するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。

:::row:::
    :::column:::
        ![ブルーム close](images/bloom-close.png)<br>
        **手順 1: すぐに使用することができます。**<br>
    :::column-end:::
    :::column:::
        ![ブルームを開く](images/bloom-open.png)<br>
        **手順 2: すぐに使えるパームアップ**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>開始ジェスチャ
HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これにより、追加の教育を必要としない instinctual の対話が可能になります。 手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。

:::row:::
    :::column:::
        ![手首ボタンの準備完了](images/wrist-button-ready.png)<br>
        **手順 1: パームアップ: 手首ボタンを表示する**<br>
    :::column-end:::
    :::column:::
        ![手首ボタンの押下](images/wrist-button-press.png)<br>
        **手順 2: 手首ボタンを押す**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>ワンきき開始ジェスチャ

> [!IMPORTANT]
> ワンきき開始ジェスチャを機能させるには、次のようにします。
>
> 1. 2019年11月の更新プログラム (ビルド 18363.1039) 以降に更新する必要があります。
> 1. 視線追跡が正常に機能するように、デバイスで目を調整する必要があります。 [Start] \ (開始 \) アイコンを見たときに orbiting のドットが表示されない場合は、デバイス上で目が調整されていません。

開始ジェスチャは、ワンハンドでのみ実行することもできます。 これを行うには、パームに接続したままにして、内部の手首の [ **開始] アイコン** を見てください。 **アイコンを見たまま** にして、親指と人差し指を一緒にピンチします。<br>
:::row:::
    :::column:::
        ![手首ボタンの準備完了](images/wrist-button-ready.png)<br>
        **手順 1: パームアップ: 手首ボタンを表示する**<br>
    :::column-end:::
    :::column:::
        ![手首ボタンのピンチ](images/wrist-button-pinch.png)<br>
        **手順 2: ボタンをクリックしてからピンチする**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>関連項目

* [本能的な操作](interaction-fundamentals.md)
* [視線](eye-tracking.md)
* [音声入力](voice-input.md)
