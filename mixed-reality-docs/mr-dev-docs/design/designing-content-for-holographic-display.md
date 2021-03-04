---
title: ホログラフィック ディスプレイのコンテンツを設計する
description: HoloLens デバイスでの holographic 表示の設計ガイドラインとベストプラクティスについて説明します。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI デザイン, holographic 表示, コンテンツデザイン, ダークテーマ, ライトテーマ, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality Toolkit, 設計, ピクセル
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759277"
---
# <a name="designing-content-for-holographic-display"></a>ホログラフィック ディスプレイのコンテンツを設計する

![Ulnar side location](images/UX_Hero_DarkTheme.jpg)

Holographic が表示されるようにコンテンツを設計する際には、最適なエクスペリエンスを実現するために考慮する必要がある要素がいくつかあります。 ここでは、いくつかの推奨事項の一覧を示し、 [色、光、およびマテリアル](color-light-and-materials.md) のページで holographic 表示の特性について詳しく説明します。

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>大きな表面で明るい色の課題 

HoloLens エクスペリエンスの研究とテストに基づいて、ディスプレイの大きな領域で明るい色を使用すると、いくつかの問題が発生する可能性があることがわかりました。 

**目の疲労** 

Holographic display は加法であるため、明るい色を持つホログラムはより多くの光を使用します。 ディスプレイの大きな領域に明るい色を使用すると、ユーザーにとって目の疲労が簡単になります。 

**手動でのオクルージョン** 

明るい色を使用すると、オブジェクトを直接操作するときにユーザーが手を見ることが難しくなります。 ユーザーは人間を見ることができないため、針とターゲットサーフェスの間の深さ/距離を認識することは困難になります。 指カーソルを使用するとこの問題を補うことができますが、それでも明るい白い面では困難な場合があります。 

![色とハンドオクルーが ](images/color_handocclusion.jpg)
 *明るい色のコンテンツバックプレートで手を見づらい*

**色の統一性**

Holographic 表示の特性により、画面上の大きな明るい領域が blotchy になることがあります。 ダーク配色を使用すると、この問題を最小限に抑えることができます。 

## <a name="design-guidelines-for-color-choices"></a>色の選択のデザインガイドライン

**UI の背景に濃い色を使用する**

ダーク配色を使用することにより、目の疲労を最小化し、直接的なやり取りに対する信頼度を高めることができます。 

![コンテンツの背景に使用される濃い色 ](images/color_dark_examples.jpg)
 *の例* コンテンツの背景に使用される暗い色の例

**Semibold または太字のフォントの太さを使用する**

HoloLens を使用すると、美しい高解像度のテキストを表示できます。 ただし、縦方向のストロークが小さいフォントサイズでジッターになる可能性があるため、光や半光などの細いフォントの重みを使用しないことをお勧めします。 

![太字または半太字のフォントの太さ (上のパネル) では、読みやすくするために ](images/color_font_examples.jpg)
 *太字または半太字のフォントの太さ (上のパネル) が向上します。*

**MRTK の HolographicBackplate マテリアルを使用する**

HolographicBackplate マテリアルは、HoloLens シェルのいくつかの UI パネルに適用されます。 その機能の1つは、パネルに基づいてユーザーが移動するときにユーザーに表示される iridescence 効果です。 バックプレートの色は、事前に定義された範囲にわたって微妙に変化し、コンテンツの読みやすさを妨げることなく、魅力的で動的な視覚効果を作成します。 この微妙な色の変化は、軽微な色の不規則性を補正するためにも役立ちます。 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>透明または半透明の UI backplate に関する課題 

![透過的 ](images/color_transparent_examples.jpg)
 *な ui の例透過 ui バックプレートの例*

**視覚的な複雑さとアクセシビリティ**

Holographic オブジェクトは物理的な環境と blend があるため、透明または半透明のウィンドウでコンテンツや UI が読みやすくなり、パフォーマンスが低下する可能性があります。 さらに、transparent holographic オブジェクトが相互に重なっていると、ユーザーが混乱を招くことがあるため、ユーザーが対話するのが困難になる可能性があります。

**パフォーマンス**

透明または半透明のオブジェクトが正しくレンダリングされるようにするには、背景に存在するオブジェクトとの間で並べ替えおよびブレンドを行う必要があります。 透過的なオブジェクトを並べ替えると CPU コストが非常に大きくなります。これは、GPU が z カリングを使用した非表示サーフェスの削除を許可しないため (つまり、 詳細テスト)。 非表示サーフェイスの削除を許可しない場合は、レンダリングされた最後のピクセルに必要な操作の数が増加します。 これにより、より多くの圧力フィルレート制約が課されます。

**深さ LSR テクノロジを使用したホログラムの安定性の問題**

Holographic の再プロジェクションやホログラムの安定性を向上させるために、アプリケーションは描画されたすべてのフレームに対して深度バッファーをシステムに送信できます。 Reprojection の深度バッファーを使用する場合は、表示されるすべての色に対応する深度に対して深度バッファーを記述する必要があります。 深度値を持つすべてのピクセルにも色の値が必要です。 上記のガイダンスに従っていない場合、有効な深度情報のないレンダリングされたイメージの領域が、成果物を生成する方法で再投影される可能性があります。これは、多くの場合、波のような歪みとして表示されます。


## <a name="design-guidelines-for-transparent-elements"></a>透過的な要素のデザインガイドライン

**不透明な UI の背景を使用する**

既定では、透明または半透明のオブジェクトは、適切なブレンドを可能にするための深度を書き込みません。 この問題を軽減するには、不透明なオブジェクトを使用して、透明なオブジェクトが不透明なオブジェクト (不透明な backplate の前面にある半透明のボタンなど) の近くに表示されるようにする、半透明なオブジェクトを強制的に書き込み (すべてのシナリオでは適用しない)、またはフレームの最後に深さの値のみを提供する

MRTK-Unity 内のソリューション: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity  

純色と不透明なバックプレートを使用することにより、読みやすさと相互作用の信頼を確保できます。

**影響を受けるピクセル数を最小限に抑える**

プロジェクトで透過的なオブジェクトを使用する必要がある場合は、影響を受けるピクセル数を最小限に抑えてください。 たとえば、オブジェクトが特定の条件下でのみ表示される場合 (加法グロー効果など) は、オブジェクトが完全に非表示になったときに、そのオブジェクトを無効にします (加法の色を黒に設定するのではなく)。 アルファマスクを持つクワッドを使用して作成された単純な2D 図形の場合は、代わりに不透明なシェーダーを使用して図形のメッシュ表現を作成することを検討してください。 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用の濃い UI の例 (Mixed Reality Toolkit)

**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、濃色配色に基づく多数の UI 構成ブロックの例が用意されています。

* [Near メニュー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [ダイアログ](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [ハンドメニュー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a>関連項目

* [色、ライト、素材](color-light-and-materials.md)
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
