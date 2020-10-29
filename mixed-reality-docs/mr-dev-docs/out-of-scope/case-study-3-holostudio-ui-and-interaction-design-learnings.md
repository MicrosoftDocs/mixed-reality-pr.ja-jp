---
title: ケーススタディ-3 HoloStudio UI と相互作用設計学習
description: HoloStudio UI と操作設計の学習
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: 55fc9cea93582612abb5e0f8955deb5629da3093
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687586"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>ケーススタディ-3 HoloStudio UI と相互作用設計学習

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) は、HoloLens 用の最初の Microsoft アプリの1つでした。 このため、3D UI と対話デザインのための新しいベストプラクティスを作成する必要がありました。 これは、多数のユーザーテスト、プロトタイプ、および試用とエラーによって行われました。

私たちは、この種の調査を行うためのリソースがすべてのユーザーに提供されているわけではありません。 Holographic Designer、Marcus Ghaly、HoloStudio の開発中に学習した3つのことを、HoloLens アプリの UI と相互作用設計について共有しています。

## <a name="watch-the-video"></a>ビデオを見る

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>問題 #1: ユーザーの作成を避けたい

最初は、現実の世界で見たように、HoloStudio でワークベンチを四角形として設計しました。 問題は、ユーザーが席に座っているときや、コンピューターの前に座っているときでも、ワークベンチを動かさずに3D の作成を調べることができなかったことを示す、経験のある期間があることです。

![HoloStudio dissuaded のワークベンチの四角形のデザインは、すべての側からの作成を左右に移動できません。](images/rectangular-workbench-500px.jpg)

私たちは、ワークベンチを丸めるための洞察を得ました。これにより、"正面" や明確な場所がなくなります。 これをテストしたところ、突然のユーザーが自分で開発を行ってきました。

![円形ワークベンチの設計では、ユーザーの作成をすべての方法で行うことをお勧めします。](images/circular-workbench-500px.jpg)

**学習内容**

常に、ユーザーにとって快適なことを考えてください。 これらの物理領域を利用することは、HoloLens の優れた機能であり、他のデバイスでは実行できないものです。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>問題 #2: モーダルダイアログが holographic フレームの外になることがあります。

場合によっては、ユーザーがアプリで注意する必要があるものとは異なる方向を探すことがあります。 PC では、ダイアログをポップアップするだけで済みますが、3D 環境で他のユーザーの顔でこの操作を行うと、ダイアログが表示されているように感じられる可能性があります。 メッセージを読み取るために必要ですが、性質はそのメッセージを取得しようとしています。 この反応はゲームをプレイしている場合には非常に便利ですが、作業用に設計されたツールでは理想的とは言えません。

いくつかの点を試した後、最終的には、ダイアログの "思考バブル" システムを使用して、ユーザーがアプリケーションで注意が必要な箇所に従うことができる tendrils を追加しました。 また、tendrils のパルスも作成しました。これは、ユーザーがどこに移動するかを把握できるように、方向性の意味を暗示しています。

!["思考バブル" システムには、方向を意味する発する tendrils が含まれていました。これは、アプリでの注意が必要な場所をユーザーに導きます。](images/thought-bubble-500px.jpg)

**学習内容**

3D では、ユーザーに注意を払う必要があることを警告するのは非常に困難です。 [空間サウンド](../design/spatial-sound.md)、光線、または思考バブルなどのアテンションダイレクタを使用すると、ユーザーが必要な場所に移動する可能性があります。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>問題 #3: 他のホログラムによって UI がブロックされることがある

ユーザーがホログラムとそれに関連付けられた UI コントロールを操作しようとしていても、別のホログラムが前面にあるためにビューがブロックされている場合があります。 HoloStudio の開発中に、試用版とエラーを使用して、このソリューションを提供しました。

![ホログラムに関連付けられている UI コントロールは、それとユーザーが装着した HoloLens の間に別のホログラムがある場合、ブロックされる可能性があります。](images/ui-blocked-500px.jpg)

UI コントロールはユーザーの近くに移動しようとしました。ブロックされることはありませんでしたが、ユーザーは、遠くにいるホログラムを同時に見ている間に、ユーザーが自分の近くにいたコントロールを見ても慣れていないことがわかりました。 ただし、最も近いホログラムの前にあるコントロールをユーザーに移動した場合は、影響を受けているホログラムから切り離されているように感じられます。

最後に、UI コントロールのゴーストを終了し、ユーザーから関連付けられているホログラムと同じ距離に配置します。そのため、両方とも接続されています。 これにより、ユーザーは、隠されている場合でもコントロールを操作できます。

![解決策: UI コントロールを非実体にします。このコントロールは、コントロールとの対話を許可し、それが影響を与えていたホログラムに接続するようにしました。](images/ghosting-ui-500px.jpg)

**学習内容**

ユーザーは、ブロックされている場合でも UI コントロールに簡単にアクセスできる必要があります。そのため、ユーザーが自分のホログラムが実際のどこにあるかに関係なく、ユーザーがタスクを完了できるようにする方法を確認してください。

## <a name="about-the-author"></a>著者について

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Holographic デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目
* [本能的な操作](../design/interaction-fundamentals.md)
