---
title: ケーススタディ-Lowe のキッチンからの教訓
description: HoloLens チームは、Lowe の HoloLens プロジェクトから派生したベストプラクティスの一部を共有したいと考えています。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Lowe、HoloLens、キッチン、ケーススタディ
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687439"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>ケーススタディ-Lowe のキッチンからの教訓

HoloLens チームは、Lowe の HoloLens プロジェクトから派生したベストプラクティスの一部を共有したいと考えています。 以下は、Satya の 2016 Ignite 基調講演で示されている Lowe の HoloLens のビデオです。
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe の HoloLens のベストプラクティス

2つのビデオでは、2016年4月から2つの Lowe の店舗に含まれていた Lowe の HoloLens パイロットから得られたベストプラクティスについて説明しています。 主なトピックは次のとおりです。
* モバイルデバイスのパフォーマンスを最大にする
* Full holographic フレームを使用して UX メソッドを作成する (2 回目の話)
* 有効桁数の配置 (2 番目のトーク)
* Shared holographic エクスペリエンス (2 番目の会話)
* 顧客との対話 (2 回目の話)

## <a name="video-1"></a>ビデオ1

**モバイルデバイスのパフォーマンスを最大に** するHoloLens は、デバイスですべての処理が行われるならではデバイスです。 これにはモバイルプラットフォームが必要であり、モバイルアプリケーションの作成と同様の考え方が必要です。 Microsoft では、ユーザーに delicious エクスペリエンスを提供するために、HoloLens アプリケーションで60FPS を維持することをお勧めします。 FPS が低いと、ホログラムが不安定になる可能性があります。

HoloLens で開発するときに注目すべき重要な点のいくつかは、カスタムシェーダー ( [Hololens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)で無料で利用可能) を使用した、資産の最適化/確認です。 もう1つの重要な考慮事項は、プロジェクトの最初からフレームレートを測定することです。 プロジェクトによっては、アセットを表示する順序が大きな共同作成者である場合もあります。
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>ビデオ2

**完全な holographic フレームを使用して UX メソッドを作成** する物理的な世界でのホログラムの配置について理解しておくことが重要です。 Lowe を使用すると、さまざまな UX メソッドについて説明します。これにより、ユーザーは、ホログラムの大規模な環境を見ながら、最新の状態にすることができます。

**有効桁数の配置** Lowe のシナリオでは、ホログラムを物理的なキッチンに正確に配置することが最も重要でした。 これらの手法については、ユーザーの物理的な環境が変更されたことを仕向けるするエクスペリエンスを保証するのに役立ちます。

**共有 holographic エクスペリエンス** 結合は、Lowe のエクスペリエンスを使用する主な方法です。 1人のユーザーがカウンターを変更すると、他のユーザーが変更を確認できます。 この "共有エクスペリエンス" を呼び出しました。

**顧客との対話** Lowe のデザイナーは HoloLens を使用していませんが、顧客に表示される内容を確認する必要があります。 UWP アプリケーションで顧客が見ている内容をキャプチャする方法を示します。
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
