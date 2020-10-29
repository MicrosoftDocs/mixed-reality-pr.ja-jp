---
title: ケース スタディ - Mixed Reality で穴から覗く
description: このケーススタディでは、HoloLens に "マジックウィンドウ" 効果を実装する方法について説明します。これにより、ユーザーは、壁の背後、床の下、および実際の環境内の仮想化について確認できます。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、マジックウィンドウ、視差
ms.openlocfilehash: 84af124cc69e03b3502cee55c694b11ff5c9433b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687426"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>ケース スタディ - Mixed Reality で穴から覗く

混合現実と、Microsoft HoloLens で実行できることを考える人は、通常、「どのオブジェクトをどのようにしてルームに追加できるか」といった質問になります。 または、「どのようにして自分のスペースにレイヤーを持たせることができますか」ということです。 ここでは、同じテクノロジを使用して、実際の物理的なオブジェクトを検索したり、そこから見たりすることができる別の領域を強調することができます。

## <a name="the-tech"></a>技術

**[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 内の壁を異星人、fought で壁を突破した **[場合、また](case-study-creating-an-immersive-experience-in-fragments.md)** は **[2015 の E3 でハロー5エクスペリエンス](https://www.youtube.com/watch?v=QDw5QjDtFy8)** の unsc 無限大の hangar を確認するのに十分な経験がある場合は、私が話していることを見てきました。 想像に応じて、この視覚的なトリックを使用して、drywall に一時的な穴を置いたり、疎 floorboard でワールドを隠したりすることができます。

![RoboRaid は、3次元パイプと、壁の背後にあるその他の構造を追加します。これは、侵入の中断として作成された穴によってのみ表示されます。](../develop/unity/images/roboraid-640px.png)

RoboRaid は、3次元パイプと、壁の背後にあるその他の構造を追加します。これは、侵入の中断として作成された穴によってのみ表示されます。

HoloLens でこれらの固有のホログラムの1つを使用すると、アプリでは、実際のウィンドウを通じて自然に表示されるのと同じ方法で、壁の背後やフロアを介してコンテンツの錯覚を提供できます。 左側に移動すると、右側に何があるかを確認できます。 詳細については、さらに詳しく見ていきましょう。 大きな違いは、実際の穴によって、魔法の holographic コンテンツに stubbornly ことができないことです。 (バックログにタスクを追加します)。

## <a name="behind-the-scenes"></a>バックグラウンド処理

このトリックは、2つの効果を組み合わせたものです。 まず、holographic コンテンツが "空間アンカー" を使用して世界にピン留めされます。 アンカーを使用してそのコンテンツを "世界ロック" にすることは、移動したり、基になる空間マッピングシステムが部屋の3D モデルを更新したりしても、周囲の物理的なオブジェクトからは視覚的にずれないことを意味します。

2つ目は、holographic コンテンツが非常に特殊な領域に視覚的に限定されているので、実際にはその穴だけを見ることができるからです。 このオクルージョンは、トリックを販売する論理的な穴、ウィンドウ、または入室を探す必要があるために必要です。 ほとんどのビューがブロックされていなくても、secret Jurassic ディメンションへの領域の亀裂は、適切に配置されていない恐竜のように見えます。

![これは実際のスクリーンショットではありませんが、MR 基本101の secret 黄泉が HoloLens を検索する方法を示しています。 黒いエンクロージャは表示されませんが、仮想の穴でコンテンツを見ることができます。 (実際のデバイスを参照している場合、フロアはそれ以上に見えなくなるように見えます。これは、それほど離れているように見えます。](images/origamiholecomposited-640px.png)

これは実際のスクリーンショットではありませんが、 [MR 基本 101](../develop/unity/tutorials/holograms-101.md) のシークレットが HoloLens でどのように見えるかを示しています。 黒いエンクロージャは表示されませんが、仮想の穴でコンテンツを見ることができます。 (実際のデバイスを参照している場合、フロアはそれ以上に見えなくなるように見えます。これは、それほど離れているように見えます。

### <a name="world-locking-holographic-content"></a>ワールド-holographic コンテンツのロック

Unity では、WorldAnchor コンポーネントを追加するのと同じように、holographic コンテンツを世界中にロックしたままにすることができます。

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor コンポーネントは、近くの物理オブジェクトとの間で安定した状態を維持するために、そのオブジェクト (階層内のそのオブジェクトの下) の位置と回転を絶えず調整します。 コンテンツを作成するときは、オブジェクトのルートピボットがこの仮想ホールの中央に配置されるように作成します。 (オブジェクトのピボットが壁の中で深い場合、位置と回転の微妙な微調整ははるかに目立つようになり、穴が非常に安定していない可能性があります)。

### <a name="occluding-everything-but-the-virtual-hole"></a>仮想ホールを除いてすべてを Occluding

ビューを選択的にブロックして、壁面で非表示にする方法はさまざまです。 最も簡単なのは、HoloLens が加法ディスプレイを使用するという事実を利用することです。つまり、完全に黒のオブジェクトは非表示になります。 これは、特殊なシェーダーや素材を使用せずに Unity で行うことができます。黒の素材を作成して、コンテンツ内のボックスを持つオブジェクトに割り当てるだけです。 3D モデリングを実行したくない場合は、いくつかの既定の Quad オブジェクトを使用して、わずかに重なります。 このアプローチにはいくつかの欠点がありますが、動作を実現するための最も簡単な方法ですが、後でリファクタリングする可能性があると思われる場合でも、非常に忠実度の高い概念実証を利用することができます。

上記の "ブラックボックス" アプローチの大きな欠点の1つは、写真が適切ではないことです。 お客様の影響は HoloLens の表示によって完璧に見える場合がありますが、どのスクリーンショットを使用しても、壁やフロアの残りの部分ではなく、大きな黒のオブジェクトが表示されます。 その理由は、物理的なハードウェアとスクリーンショットは、複合ホログラムと現実が異なることです。 それでは、いくつかの偽の数値に迂回てみましょう。

*偽の算術アラートです。これらの数値と数式は、正確なメトリックではなく、ポイントを示すことを目的としています。*

HoloLens を通じて表示するもの:

```
( Reality * darkening_amount ) + Holograms
```

スクリーンショットとビデオには次のような内容が表示されます。

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

英語の場合: HoloLens を通じて表示されるものは、(サングラスを通じてのように) 暗い現実の単純な組み合わせで、アプリが表示する必要のあるホログラムです。 しかし、スクリーンショットを撮ると、ピクセルごとの透明度の値に応じて、カメラのイメージがアプリのホログラムとブレンドされます。

この問題を回避する方法の1つとして、"ブラックボックス" の素材を変更して、深度バッファーに書き込むだけで、他の不透明な素材をすべて使用して並べ替えることができます。 この例については、GitHub の [MixedRealityToolkit ファイル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)を確認してください。 関連する行がここにコピーされます。

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

("Offset 50, 100" という行は、関連のない問題に対処するものであるため、そのままにしておくとよいでしょう)。

そのような非表示の遮蔽物を実装すると、アプリでは、画面と mixed reality のスクリーンショットで適切に見える箱を描くことができます。 ボーナスポイントについては、このボックスのパフォーマンスをさらに向上させることができます。これには、少しの見えないピクセルを描画することができますが、それは雑草になる可能性があり、通常は必要ありません。

![次に示すのは、occluding ボックスの外側の部分を除いて、Unity によって描画される MR の基本101のシークレットです。 黄泉の方のために、この図は箱の中央にあります。これにより、穴をできるだけ安定した状態に保つことができます。](images/underworld-occluded-640px.png)

次に示すのは、occluding ボックスの外側の部分を除いて、Unity によって描画される [MR の基本 101](../develop/unity/tutorials/holograms-101.md) のシークレットです。 黄泉の方のために、この図は箱の中央にあります。これにより、穴をできるだけ安定した状態に保つことができます。

## <a name="do-it-yourself"></a>自分で実行する

HoloLens を所有していて、その効果を試す必要がある場合は、 最も簡単な方法は (コーディングが不要)、無料の3D ビューアーアプリをインストールし、 [GitHub で提供した fbx ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) して、部屋に花ポットモデルを表示することです。 これを HoloLens に読み込んで、仕事ができていることを確認できます。 モデルの前にいる場合は、小さな穴だけを見ることができます。他のすべての要素は非表示になります。 モデルを他の側から見ると、完全に消えます。 3D ビューアーの移動、回転、およびスケールのコントロールを使用して、いくつかのアイデアを生成するために考えられる垂直方向の表面に仮想ホールを配置します。

![Unity エディターでこのモデルを表示すると、flowerpot の周りに大きな黒いボックスが表示されます。 HoloLens では、ボックスが消え、マジックウィンドウ効果が提供されます。](images/magicwindowflowerpotineditor.png)

Unity エディターでこのモデルを表示すると、flowerpot の周りに大きな黒いボックスが表示されます。 HoloLens では、ボックスが消え、マジックウィンドウ効果が提供されます。

この手法を使用するアプリをビルドする場合は、「 [Mixed Reality チュートリアル](../develop/unity/tutorials.md)」の[MR 基本101チュートリアル](../develop/unity/tutorials/holograms-101.md)をご覧ください。 第7章は、隠れている (上の図のように) 隠れた黄泉を示すフロアの爆発で終わります。 チュートリアルを行ったのは退屈ですか。

ここでは、次のアイデアを参考にしてください。
* 仮想ホール内のコンテンツを対話形式で作成する方法について考えてみましょう。 ユーザーが壁を越える影響を与えることで、このトリックによって得られる不思議な意義を高めることができます。
* オブジェクトを使用して既知の領域に戻る方法を考えてみましょう。 たとえば、holographic 穴をコーヒーテーブルに配置し、その下にフロアを表示するにはどうすればよいでしょうか。

## <a name="about-the-author"></a>著者について

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>シニアソフトウェアエンジニア @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目
* [MR の基本 101:デバイスを使用した完全なプロジェクト](../develop/unity/tutorials/holograms-101.md)
* [座標系](../design/coordinate-systems.md)
* [空間アンカー](../design/spatial-anchors.md)
* [空間マッピング](../design/spatial-mapping.md)
