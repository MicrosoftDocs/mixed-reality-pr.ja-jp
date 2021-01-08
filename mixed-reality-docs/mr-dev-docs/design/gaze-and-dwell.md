---
title: 視線入力とドウェル
description: Mixed reality アプリケーションの視線および熟考入力モデルの一般的な概要を説明します。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、熟考、相互作用、設計、視線追跡、ヘッド追跡、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 2daeea996251b1220ee4753567b42117fbb2126c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007642"
---
# <a name="gaze-and-dwell"></a>視線入力とドウェル

工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。
また、音声コマンドは特定のコンテキストでは信頼できない場合もあります。たとえば、非常に大きな条件が発生した場合などです。
宝石と熟考は、HoloLens でのヘッドアップとハンズフリーの作業を行うための使い慣れた、簡単なマスタメカニズムを提供します。
また、宝石と熟考は、運用環境でのノイズ干渉や無音の制約に依存しない優れたフォールバックです。
_熟考_ と [熟考](gaze-and-dwell-head.md)の2つのバリエーションと、[視線と熟考](gaze-and-dwell-eyes.md)を区別しています。

## <a name="scenarios"></a>シナリオ

熟考は、人間の手が他のタスクと共に忙しい場合や、環境やソーシャルの制約のために音声が 100% reliable or available ではない場合に威力を持っています。
良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。
その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。
ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。
熟考を使用すると、HoloLens を使用するユーザーは、ワークフローを中断することなく、参照資料を自信を持ってナビゲートできます。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>入力モデル</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>頭の視線入力とドウェル</td>
        <td>✔️ 推奨</td>
        <td>✔️ 推奨</td>
        <td>✔️ 推奨</td>
    </tr>
     <tr>
        <td>目の視線入力とドウェル</td>
        <td>❌ 使用できません</td>
        <td>✔️ 推奨</td>
        <td>❌ 使用できません</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>関連項目

* [視線ベースの操作](eye-gaze-interaction.md)
* [HoloLens 2 上の視線追跡](eye-tracking.md)
* [視線入力とコミット](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - ジェスチャ](gaze-and-commit.md#composite-gestures)
* [手 - ポイントとコミット](point-and-commit.md)
* [本能的な操作](interaction-fundamentals.md)
* [音声入力](voice-input.md)
