---
title: Billboard と Tag-along
description: Billboarding を使用するオブジェクトは、常にユーザーに顔を合わせて向きます。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、billboarding、タグ
ms.openlocfilehash: 266fb314ae4fccdc25e94b20d04262666be5a1b6
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685162"
---
# <a name="billboarding-and-tag-along"></a>Billboard と Tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Billboarding とは

Billboarding は、混合現実のオブジェクトに適用できる動作の概念です。 Billboarding を使用するオブジェクトは、常にユーザーに顔を合わせて向きます。 これは、ユーザーが移動した場合に、ユーザーの環境に配置されている静的オブジェクト (ワールドロック) が隠されたり、読み取り不可能になったりするテキストおよび menuing システムに特に役立ちます。

Billboarding が有効になっているオブジェクトは、ユーザーの環境で自由に回転できます。 また、設計上の考慮事項に応じて、1つの軸に制限することもできます。 Billboarded オブジェクトは、他のオブジェクトに近すぎるか、または HoloLens によってスキャンされたサーフェイスが終了した場合に、自身をクリップまたは occlude することができます。 これを回避するには、billboarding に対して有効にした軸で回転したときにオブジェクトが生成する総フットプリントを考えてください。

<br>

---
## <a name="what-is-a-tag-along"></a>タグとは何ですか。

タグに加えて、ホログラムに追加できる動作の概念です。 タグに沿ったオブジェクトは、ユーザーが快適に対話できる範囲内を維持しようとします。

![HoloLens のピンパネルは、タグに沿った動作の優れた例です。](images/tagalong-1000px.jpg)<br>
*HoloLens の [スタート] メニューは、タグに沿った動作の優れた例です。*

タグに沿ったオブジェクトには、動作を微調整できるパラメーターがあります。 コンテンツは、ユーザーの環境内を移動しながら、必要に応じてユーザーの視野を越えることができます。 ユーザーが移動すると、コンテンツは、ユーザーの移動速度によって、コンテンツが一時的に非表示になる可能性があることによって、ユーザーの周囲の内側に置かれます。 ユーザーがタグに沿って gazes すると、より完全に表示されます。 コンテンツは常に "一目でわかる" と考えられるので、ユーザーがコンテンツの方向を忘れないようにします。

追加のパラメーターを使用すると、タグに沿ってオブジェクトをラバーバンドでユーザーの頭部に接続することができます。 ダンパーの加速または減速により、オブジェクトに対して重みが与えられ、物理的に存在するようになります。 この spring behavior は、ユーザーがタグを操作する方法の正確なメンタルモデルを作成するのに役立つ affordance です。 オーディオは、ユーザーがタグに沿ってオブジェクトを持っている場合に、追加の affordances を提供するのに役立ちます。 オーディオは移動速度を強調する必要があります。ファーストヘッドターンでは、自然な速度での再生では、効果がある場合は最小限のオーディオを使用します。

実際にヘッドにロックされたコンテンツと同様に、タグに沿ってオブジェクトを使用すると、ユーザーのビューで非常に大きな動きがあるか、またはばねが非常に大きくなると、非常に多くのことを行うことができます。 ユーザーが見てすぐに停止すると、それらが停止したことがわかります。 これらのバランスによって、ヘッドが旋回を停止したことが通知され、その構想によって世界が停止していることがわかります。 ただし、ユーザーが停止したときにタグに沿って移動し続けると、その状態が混乱する可能性があります。

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Billboarding とタグ-Unity の MRTK (Mixed Reality Toolkit)
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、Billboarding とタグに沿った動作のスクリプトが用意されています。 Billboard.cs スクリプトを任意のオブジェクトに割り当てて、billboarding の動作を追加し、オブジェクトが常に顔になるようにします。 タグに沿った動作を追加するには、RadialView.cs スクリプトを使用します。 Lerping time、distance、次数などのさまざまなオプションを調整できます。

* [MRTK-放射状ビューのソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-ビルボードスクリプト](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>関連項目

* [カーソル](cursors.md)
* [ハンド レイ](point-and-commit.md)
* [ボタン](button.md)
* [対話可能なオブジェクト](interactable-object.md)
* [境界ボックスとアプリ バー](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [ハンド メニュー](hand-menu.md)
* [メニューの近く](near-menu.md)
* [オブジェクト コレクション](object-collection.md)
* [音声コマンド](voice-input.md)
* [キーボード](keyboard.md)
* [ヒント](tooltip.md)
* [スレート](slate.md)
* [スライダー](slider.md)
* [シェーダー](shader.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
* [進行状況を表示する](progress.md)
* [表面吸着](surface-magnetism.md)
