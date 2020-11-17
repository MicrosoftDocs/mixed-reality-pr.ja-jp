---
title: 月着陸船
description: LunarModule は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 このプロジェクトでは、2つのききの追跡と Xbox コントローラー入力を使用して HoloLens の基本ジェスチャを拡張する方法を学習できます。また、画面のマッピングとプレーンに反応するオブジェクトを作成し、単純なメニューシステムを検索して実装することができます。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, サンプルアプリ, 設計, MRTK, Mixed Reality ツールキット, Unity, サンプルアプリ, アプリの例, オープンソース, Microsoft Store, HoloLens, Mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット
ms.openlocfilehash: ad5c544b9c164ef0d85eb3217685d6f96bb86367
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677467"
---
# <a name="lunar-module"></a>月着陸船

>[!NOTE]
>この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。 設計関連の記事とコードは、新しい検出を行うと進化します。

[旧暦モジュール](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 このプロジェクトでは、2つのききの追跡と Xbox コントローラー入力を使用して HoloLens の基本ジェスチャを拡張する方法を学習できます。また、画面のマッピングとプレーンに反応するオブジェクトを作成し、単純なメニューシステムを検索して実装することができます。 プロジェクトのすべてのコンポーネントは、独自の mixed reality アプリエクスペリエンスで使用できます。

## <a name="demo-video"></a>デモ ビデオ 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Mixed Reality キャプチャを使用して HoloLens 2 で記録

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Windows Mixed Reality の再考クラシックエクスペリエンス

この大気では、Apollo モジュールの小さな ship 似が、次のようにギザギザになっています。 Fearless パイロットは、適切なランディングエリアを特色としています。 降下は困難なですが、これまでに何度も実行されています。

![Atari の1979太陰暦からの元のインターフェイス](images/640px-atari-lunar-lander.png)<br>
*Atari の1979太陰暦からの元のインターフェイス*

[太陰暦](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) は、プレーヤーが月のゲームを太陰暦の平らな位置にパイロットしようとするアーケードクラシックです。 1970年に誕生した人は、このベクトルに接着されているアーケードの中で、空になっていることが多いと思われることでしょう。 プレーヤーが発送先を目的のランディング領域に移動するにつれて、地形が拡大縮小され、さらに詳細な情報が表示されます。 成功は、水平および垂直速度の安全なしきい値内での着陸を意味します。 ランディングと残りの燃料に対してポイントが与えられ、ランディング領域のサイズに基づく乗数が使用されます。

ゲームのアーケード時代は、ゲームプレイとは別に、コントロールスキームの革新的なイノベーションをもたらしていました。 最も単純な4方向のジョイスティックとボタンの構成 (アイコンの [Pac](https://en.wikipedia.org/wiki/Pac-Man)で見られます) から、遅延90年代と 00s (ゴルフシミュレーターやレールの shooters など) に見られる、非常に特殊で複雑なスキームを選択します。 太陰暦コンピューターで使用される入力方式は、おもしろいの魅力と immersion という2つの理由で特に重要です。

![Atari の旧暦コンソール](images/atariconsole.png)<br>
*Atari の旧暦コンソール*

なぜ Atari と、他の多くのゲーム会社が入力の再考を決定するのでしょうか。

アーケードの子供たちは、最新の flashiest マシンによって自然に intrigued されます。 しかし、太陰暦では、整備士のような斬新な入力ができます。

太陰暦では、2つのボタンを使用して、出荷の左と右を回転し、 **推力レバー** を使用して、出荷によって生成される推力の量を制御します。 このレバーは、通常のジョイスティックが提供できない一定レベルの finesse をユーザーに提供します。 また、最新の航空コックピットに共通するコンポーネントでもあります。 Atari は、ユーザーが旧暦モジュールを実際に操縦していると感じていることをユーザーにこちらさせる必要がありました。 この概念は、 **tactile immersion** と呼ばれています。

Tactile immersion は、繰り返し実行するアクションの実行による sensory フィードバックのエクスペリエンスです。 この場合、目に見えるスロットルレバーと回転を調整するための反復的なアクションによって、そのプレーヤーが、シュートザムーンの表面に着陸する行為につながります。 この概念は、"flow" のテーマ概念に関連付けることができます。 チャレンジと報酬が適切に組み合わされたタスク内でユーザーが完全に吸収されている場合、またはより単純に "ゾーン内" にある場合は、

ほとんどの場合、mixed reality の immersion の最も目立つ種類は空間 immersion です。 現実には、このようなデジタルオブジェクトが現実の世界に存在することを信じています。 私たちは、環境内のホログラムをからし、環境全体とエクスペリエンスを空間的に専念しています。 これは、Atari が tactile immersion と同様に、このエクスペリエンスで他の種類の immersion を使用できないという意味ではありません。

## <a name="designing-with-immersion"></a>Immersion を使用した設計

更新された容量続編に tactile immersion を適用する方法はありますか。 入力方式に取り組む前に、3次元空間のゲームコンストラクトに対処する必要があります。

![HoloLens での surface マッピングの視覚化](images/surfacemapping.png)<br>
*HoloLens での空間マッピングの視覚化*

ユーザーの周囲を活用することによって、旧暦モジュールを着陸するための無限の地形オプションが効果的に得られます。 ゲームを元のタイトルに最もよく似たものにするために、ユーザーは環境内でさまざまな問題のあるランディングパッドを操作して配置する可能性があります。

![旧暦モジュールを操縦する](images/640px-lm-hero.jpg)<br>
*旧暦モジュールを操縦する*

ユーザーに入力スキームの学習、出荷の制御、および移動するための小さなターゲットを要求することは、よく聞かれます。 ゲームエクスペリエンスが成功すると、チャレンジと報酬が適切に組み合わされます。 ユーザーは、ユーザーが HoloLens によってスキャンされたサーフェイス上のユーザー定義領域に正常に配置されるようにすることをお勧めします。 ユーザーがゲームのハングを取得すると、それに応じて難易度を上げることができます。

### <a name="adding-input-for-hand-gestures"></a>ハンドジェスチャの入力の追加

HoloLens の基本入力には、2つのジェスチャ ( [エアタップとブルーム](../../design/gaze-and-commit.md#composite-gestures)) しかありません。 ユーザーは、コンテキストのニュアンスや特定のジェスチャの一覧を記憶する必要がありません。これにより、プラットフォームのインターフェイスが汎用性があり、学習が容易になります。 システムではこれら2つのジェスチャしか公開されませんが、デバイスとしての HoloLens は、一度に2人を追跡することができます。 ここでは、旧暦の言語は [イマーシブアプリ](../../design/app-model.md) です。これは、ジェスチャの基本セットを拡張して2人の手を活用し、旧暦モジュールナビゲーション用に独自の適切な tactile 手段を追加できることを意味します。

元の制御スキームに戻り、 **推力と回転を解決する必要** があります。 新しいコンテキストでの回転という注意は、追加の軸を追加します (技術的には2ですが、Y 軸は着陸にとって重要ではありません)。 2つの異なる出荷の移動は、自然にそれぞれの手にマップされるようにします。

![すべての3つの軸で lander を回転させるジェスチャをタップしてドラッグします](images/module-handdrag.gif)<br>
*すべての3つの軸で lander を回転させるジェスチャをタップしてドラッグします*

**逆噴射**

元のアーケードコンピューターのレバーが値のスケールにマップされている場合、レバーが大きくなると、より多くの推力が出荷に適用されました。 ここで指摘する重要な点は、ユーザーが制御を手にして目的の値を維持できることです。 タップアンドドラッグ動作を効果的に使用して、同じ結果を得ることができます。 推力値は0から始まります。 ユーザーがタップしてドラッグすると、値が大きくなります。 その時点で、メンテナンスを行うことができます。 タップしてドラッグするジェスチャの値を変更すると、元の値からの差分が得られます。

**回転**

これはもう少し厄介です。 Holographic の [回転] ボタンをタップすると、非常に快適なエクスペリエンスを実現できます。 使用する物理的なコントロールがないため、この動作は、lander を表すオブジェクトを操作するか、または lander 自体を使用して行う必要があります。 タップアンドドラッグを使用したメソッドが登場しました。これにより、ユーザーは効果的に "プッシュアンドプル" できます。 ユーザーがタップして保持するたびに、ジェスチャが開始された場所のポイントが回転の起点になります。 原点からドラッグすると、ハンドの平行移動 (X、Y、Z) のデルタが変換され、lander の回転値のデルタに適用されます。 または、 *左 < > 右にドラッグし、< > 下にドラッグして、< > をスペースで戻し* ます。

HoloLens は2人を追跡できるため、回転を右側に割り当てることができ、推力は左から制御されます。 Finesse は、このゲームの成功の推進要因です。 これらの相互作用の *感覚* は、絶対に最高の優先順位です。 特に、tactile immersion のコンテキストの場合。 速度が非常に遅くなると、そのような処理は不必要に困難になります。一方、遅すぎると、awkwardly 長い時間、出荷時に "プッシュアンドプル" が必要になることがあります。

### <a name="adding-input-for-game-controllers"></a>ゲームコントローラーの入力の追加

HoloLens の手のジェスチャには、細かい設定が可能なコントロールの斬新な方法が用意されていますが、アナログコントロールから得られる "真の" tactile フィードバックはまだありません。 Xbox ゲームコントローラーに接続することで、コントロールを使用して細かい制御を維持しながら、physicality の意味を取り戻すことができます。

比較的簡単な制御スキームを Xbox コントローラーに適用するには、複数の方法があります。 元のアーケードの設定にできるだけ近い状態を維持しようとしているため、 **スロットル** は [トリガー] ボタンに最適です。 これらのボタンはアナログコントロールであり、単純な *オンとオフ* の状態を持つことを意味し、実際にはそれらの圧力の程度に反応します。 これにより、 **推力レバー** と同様のコンストラクトが生成されます。 元のゲームや手のジェスチャとは異なり、このコントロールは、ユーザーがトリガーに対するプレッシャーを止めた後に、船の推力を切ります。 それでも、元のアーケードゲームと同じ程度の finesse がユーザーに与えられます。

![左サムスティックはヨーとロールにマップされ、右サムスティックはピッチとロールにマップされます](images/thumbsticksidebyside.gif)<br>
*左サムスティックは、ヨーとロールにマップされます。右サムスティックは、ピッチとロールにマップされます*

デュアル thumbsticks は、出荷ローテーションの制御に自然に貸与されています。 残念ながら、出荷の回転に使用できる軸は3つあり、どちらも2つの軸をサポートする2つの thumbsticks があります。 この不一致は、1つのサムスティックが1つの軸をコントロールすることを意味します。または、thumbsticks の軸が重なり合っています。 以前のソリューションでは、ローカルの X と Y の値が thumbsticks によって本質的にブレンドされているので、"破損しました" と感じています。 後者のソリューションでは、どの冗長軸が最も自然であるかを調べるためにテストが必要でした。 最後のサンプルでは、左側のサムスティックに *ヨー* と *ロール* (Y 軸と x 軸)、および右サムスティックの *ピッチ* と *ロール* (Z 軸と x 軸) を使用します。 これは、 *ロール* が独立して *ヨー* と *ピッチ* との組み合わせになっているように見えます。 注として、両方の thumbsticks を *roll* に使用すると、回転値が2倍になります。これは、lander do をループさせるのにとても楽しい作業です。

このサンプルアプリでは、Windows Mixed Reality の拡張可能な入力感覚様相によって、空間認識と tactile immersion が大きなエクスペリエンスを大幅に変更する方法を示します。 太陰暦では、旧暦が40年に近づいているかもしれませんが、この小さな八角形を使用して公開される概念は、永久に存続します。 未来を練りときに、過去に見ていないのはなぜでしょうか。

## <a name="technical-details"></a>技術的な詳細

旧暦 ( [Mixed Reality Design Labs) GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)では、太陰暦モジュールサンプルアプリのスクリプトと prefabs を見つけることができます。

## <a name="about-the-author"></a>筆者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目
* [MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)
