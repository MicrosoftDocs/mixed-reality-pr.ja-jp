---
title: 開始ジェスチャ
description: 開始ジェスチャを使用して、HoloLens および Windows Mixed Reality のイマーシブヘッドセットの [スタート] メニューを呼び出す方法について説明します。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed reality、ジェスチャ、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ブルーム
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583234"
---
# <a name="start-gesture"></a>開始ジェスチャ

Start ジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。 これは、キーボードで Windows キーを押すか、Xbox コントローラーの Xbox ボタンを押すか、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。 相互作用を設計する際の競合を防ぐため、各 Mixed Reality デバイスでの予約済みシステムジェスチャに特に注意してください。

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></td>
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

HoloLens の [スタート] メニューを表示するように "ブルーム" を設計しました。これは、花開花を模したシンボリックジェスチャです。 これは、footed の相互作用、使いやすさ、および迅速な再呼び出しにとっては独特です。 ジェスチャを使用するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。

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

HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これはユーザーにとって instinctual です。 手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。

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

また、開始ジェスチャを使用できるのはワンハンドだけです。 手のひらを使って、内部の手首にある **スタートアイコン** を見てください。 **アイコンを見たまま** にして、親指と人差し指を一緒にピンチします。<br>
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