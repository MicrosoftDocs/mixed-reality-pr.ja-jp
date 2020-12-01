---
title: Unreal の UMG とキーボード
description: Unrealm Motion グラフィックスを使用して、ウィジェットから UI システムを作成する方法について説明します。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想リアリティヘッドセット、ウィジェット、UI、UMG、Unreal Motion Graphics、Unreal Engine、UE-V、UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355408"
---
# <a name="umg-and-keyboard-in-unreal"></a>Unreal の UMG とキーボード

Unreal Motion Graphics (UMG) は、メニューやテキストボックスなどのインターフェイスを作成するために使用される Unreal Engine の組み込み UI システムです。 UMG で作成されたユーザーインターフェイスは、ウィジェットで構成されます。 このガイドでは、システムキーボードを例として使用して、新しいウィジェットを作成し、ワールド空間に追加し、そのウィジェットとの対話を mixed reality で有効にする方法について説明します。 UMG の詳細については、公式の Unreal Engine の [ドキュメント](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)を参照してください。 

## <a name="create-a-new-widget"></a>新しいウィジェットを作成する

- ゲームの UI をレイアウトするウィジェットのブループリントを作成します。

![Unreal メニューからウィジェットのブループリントを追加するスクリーンショット](images/unreal-umg-img-01.png)

- 新しいブループリントを開き、パレットからキャンバスにコンポーネントを追加します。  この例では、"Input" セクションから2つのテキストボックスコンポーネントを追加しました。

![テキストウィジェットコンポーネントが強調表示され、展開されている [階層] ウィンドウのスクリーンショット](images/unreal-umg-img-02.png)

- 階層またはデザイナーウィンドウでウィジェットを選択し、[詳細] パネルでパラメーターを変更します。  この例では、テキストボックス上にカーソルを合わせると、既定の "ヒントテキスト" と濃淡の色が追加されています。これにより、ウィジェットとの対話が可能になります。  次のような操作を行うと、テキストボックスによって HoloLens の仮想キーボードがポップアップ表示されます。

![[階層] ウィンドウで変更されたパラメーターのスクリーンショット](images/unreal-umg-img-03.png)

- [詳細] パネルでは、イベントをサブスクライブすることもできます。

![[詳細] パネルのイベントのスクリーンショット](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>ワールド空間にウィジェットを追加する

- 新しいアクターを作成し、ウィジェットコンポーネントを追加して、アクターをシーンに追加します。

![ウィジェットがアタッチされているアクターのスクリーンショット](images/unreal-umg-img-05.png)

- ウィジェットの詳細パネルで、 **ウィジェットクラス** を、前に作成したウィジェットのブループリントに設定します。

![ウィジェットクラスが設定されたブループリント詳細パネルのスクリーンショット](images/unreal-umg-img-06.png)

- テキストウィジェットの場合は、[ **ハードウェア入力の受信** ] がオフになっていることを確認します。これにより、仮想キーボードからのみテキストが更新されます。

![[受信ハードウェアの入力] の [相互作用] セクションのスクリーンショットがオフになっている](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>ウィジェットの相互作用

UMG ウィジェットは、通常、マウスから入力を受け取ります。  HoloLens または VR では、同じイベントを取得するために、ウィジェットの対話コンポーネントでマウスをシミュレートする必要があります。

- 新しいアクターを作成し、 **ウィジェットの相互作用** コンポーネントを追加して、アクターをシーンに追加します。

![ウィジェットの相互作用コンポーネントが強調表示されている新しいアクターのスクリーンショット](images/unreal-umg-img-08.png)

- ウィジェット対話コンポーネントの [詳細] パネルで、[対話距離] を目的の距離に設定し、[ **相互作用ソース** ] を [ **カスタム**] に設定し、開発用に [ **デバッグの表示** ] を **true** に設定します。

![ウィジェットの相互作用とデバッグコンポーネントのプロパティのスクリーンショット](images/unreal-umg-img-09.png)

相互作用ソースの既定値は "World" で、ウィジェット相互作用コンポーネントの世界の位置に基づいて raycasts を送信する必要がありますが、AR と VR ではこのような状況が発生しないように見えます。  [デバッグの表示] を有効にして、開発中のウィジェットに hover の濃淡を追加することは、ウィジェットの相互作用コンポーネントが期待どおりに実行していることを確認するために重要です。  この回避策は、カスタムソースを使用し、ハンドレイのイベントグラフで raycast を設定することです。  

ここでは、イベントティックからこれを呼び出しています。

![イベントティックのブループリント](images/unreal-umg-img-10.png)

次に、HoloLens 入力に反応するウィジェット対話コンポーネントに仮想マウスポインターイベントを追加します。  この例では、手が grasped のときにマウスの左押しイベントを送信し、grasped がない場合はマウスの左解放イベントを送信します。

![仮想マウスポインターイベントが追加されたブループリント](images/unreal-umg-img-13.png)

これで、HoloLens 2 にアプリを展開するときに、右側から手の光が伸びることがわかります。 編集可能なテキストボックスとエアタップのいずれかでダイレクトすると、システムキーボードが手前に表示され、テキストを入力できるようになります。 
 
> [!NOTE]
> HoloLens システムキーボードには、Unreal Engine 4.26 以降が必要です。 また、アプリがデバイスで実行されている場合にのみ、アプリが Unreal エディターからヘッドセットにストリーミングされても、キーボードは表示されません。

## <a name="see-also"></a>参照:
* [Unreal の UMG ドキュメント](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Unreal の UMG チュートリアル](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
