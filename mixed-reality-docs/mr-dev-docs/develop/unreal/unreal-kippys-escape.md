---
title: Kippy のエスケープの作成
description: Unreal Engine での HoloLens 2 の Kippy のエスケープの作成については、こちらを参照してください。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、デバイスへの展開、PC、ドキュメント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
appliesto:
- HoloLens 2
ms.openlocfilehash: eaba6ea1ee77ffffb74008402eafd1f09fd822e5
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609683"
---
# <a name="the-making-of-kippys-escape"></a>Kippy のエスケープの作成

Kippy ロボットが起動され、島上に残されていることがわかります。 問題解決の hat を使用して、ロケット船への道を見つけることができます。 HoloLens 2 でストラップを利用し、Microsoft Store から [アプリをダウンロード](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) するか、GitHub から [リポジトリ](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) を複製して、Kippy ホームセーフを獲得しましょう。  

> [!IMPORTANT]
> GitHub リポジトリから Kippy のエスケープを構築している場合は、 **Unreal Engine 4.25** 以降を使用していることを確認します。

## <a name="overview"></a>概要

Kippy のエスケープは、Unreal Engine 4 と[Mixed REALITY UX Tools For Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用して構築されたオープンソースの[HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)サンプルアプリです。 この記事では、最初の原則とビジュアルデザインから、エクスペリエンスを実装して最適化するプロセスについて説明します。 MRTK UX ツールを使用した Mixed Reality アプリケーションの開発の詳細については、 [Unreal development の概要](unreal-development-overview.md)に関するトピックを参照してください。

## <a name="first-principles"></a>最初の原則 

Kippy のエスケープを作成するための設定では、 [Unreal Engine の HoloLens 2 のサポート](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、hololens 2 の機能、Mixed Reality Toolkit を強調するエクスペリエンスを作成することを目標としました。 私たちは、Unreal と HoloLens 2 で作成できることを想像するために開発者を支援したいと考えていました。  

経験に関する3つの基本原則を紹介しました。これは楽しい作業で、対話型であり、エントリの障壁が低いことが必要でした。 この経験は、初めての混合の現実ユーザーであっても、チュートリアルを実行する必要がないという直感的な経験が必要でした。  

## <a name="designing-the-game"></a>ゲームの設計 

HoloLens 2 は、今日のゲームでは、他の場所ではない設計機能にアクセスできます。 オブジェクトは、ハンドを使用して直接プッシュしたり操作したりすることができます。 これらの主な機能は、Kippy のエスケープで構築した楽しい瞬間の背後にあります。  

ゲーム設計のガイダンスとして、独自の HoloLens 2 機能を使用して、いくつかの小規模な環境シナリオを対象にしています。 アイランドは、プレーヤーの高さが異なるために調整でき、おもしろいブリッジのアイデアを提供できるため、意味がありました。 いにしえの文明のテーマには、sci テクノロジを満たしています。これは、他のユーザーが、各島によって提供される奇妙なエネルギーを利用して、廃墟による機械を構築したという考え方です。 アイランドはそれぞれ独自のルックアンドフィールを与えられており、視覚効果の作成に役立つ情報を提供しています。 モデリングとテクスチャの間で適切なバランスを取ると、描画呼び出しのパフォーマンスが低下します。そのため、この点を念頭に置いた外観が設計されています。 

![初期のゲーム設計 ](images/kippys-escape/kippys-escape-img-01.png)
 *では、エクスペリエンスがどのようなものになるかを事前に確認し* ています。

![2番目の島の2番目の島 ](images/kippys-escape/kippys-escape-img-02.png)
 *レンダリング* のレンダリング

短時間の運用スケジュール内に保持するために、浮動小文字が厳密なアニメーションサイクルを使用せずに意図と感情をキャプチャできることに同意しました。 Kippy が生まれました。 その目とミニマルなボーカルを通じていくつかの異なる式を見て、プレイヤーのエクスペリエンスを向上させます。 

![さまざまな式を目で見て Kippy](images/kippys-escape/kippys-escape-img-03.gif)

*さまざまな式を目で見て Kippy*

![ユーザーによるパズルの解決に時間がかかりすぎる場合、Kippy はユーザーにヒントを提供します。](images/kippys-escape/kippys-escape-img-04.gif)

*ユーザーによるパズルの解決に時間がかかりすぎる場合、Kippy はユーザーにヒントを提供します。*

文字と環境の設計以外にも、ゲームが楽しくなるように一丸努力をしました。 目の追跡では、ゲームの重要な部分を強調表示した素材とサウンドの属性をオフにすることができました。 空間オーディオを使用すると、プレーヤーの周囲のレベルを自宅で見ることができます。 オブジェクトの取得、ボタンのプッシュ、およびスライダーの操作を行うことで、革新的なプレーヤーのエンゲージメントを実現できます。 これらの接続ポイントが自然に認識されるようにすることが重要でした。 

![ブリッジケーブルの端は、ユーザーが自分の手に近づいたときにグローします。](images/kippys-escape/kippys-escape-img-05.gif)

*ブリッジケーブルの端は、ユーザーが自分の手に近づいたときにグローします。*

## <a name="building-the-game-mechanics"></a>ゲーム機構の構築 

Kippy のエスケープは、ゲームをインタラクティブにするために、混合現実 UX ツールコンポーネントに大きく依存しています。つまり、手作業でアクター、境界コントロール、マニピュレーター、スライダー、およびボタンを使用します。   

[ハンドインタラクションアクター](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html)は、ホログラムの直接および遠くの操作の両方を可能にします。 Kippy のエスケープの開始時に、ユーザーにゲームの場所を設定する機会が与えられます。 ユーザーの palm から手のひらを使用すると、以下の gif に示すように、はるかに離れた大きなホログラムを簡単に操作できるようになります。  

![ハンド相互作用アクター gif](images/kippys-escape/kippys-escape-img-06.gif)

プレースホルダーシーン自体は、UX ツールの [境界制御](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) コンポーネントを使用してドラッグアンドローテーションすることができます。  

2番目の島では、ユーザーは gem を選択し、対応するスロットに配置する必要があります。 Gem には、ユーザーが選択して下に配置できるようにする [マニピュレーター](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) が関連付けられています。 

![マニピュレーターの例 gif](images/kippys-escape/kippys-escape-img-07.gif)

[Pressable ボタン](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)は、3つ目の島で使用するために爆弾を立ち上げる鍵です。  

![Pressable button の例 gif](images/kippys-escape/kippys-escape-img-08.gif)

4つ目の島に [スライダー](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) コンポーネントが表示され、最終的なブリッジが発生します。  

![スライダーコンポーネントの例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>HoloLens 2 の最適化 

モバイルデバイスで実行するように構築された経験があれば、パフォーマンスを監視することが重要です。 Unreal 4.25 には、モバイルマルチビューをサポートするための主要な更新プログラムが含まれています。これにより、レンダリングのオーバーヘッドが大幅に減少し、フレームレートが増幅されます。 最適化の際に、非 Real の HoloLens 2 開発に対して推奨される他の [パフォーマンス設定](performance-recommendations-for-unreal.md) を確認することをお勧めします。  

物理オブジェクトのパフォーマンスは依然として高くなります。そのため、いくつかの巧妙な回避策が使用されていました。 たとえば、3番目の "ブリッジ" では、階段を妨げているいくつかのごみが必要です。 デトネーションは、物理的なオブジェクトとして石に影響を与えるのではなく、スワップをトリガーし、固定のパーティクル効果のために静的石を切り替えます。 

![HoloLens 2 gif 用に最適化された例](images/kippys-escape/kippys-escape-img-10.gif) 

また、次のようにして、400 ~ 260 の描画呼び出しを削減します。 
* メッシュの複雑さの軽減
* メッシュの結合
* 初期の動的な光源要素の一部を削除しています

他にも可能なことがありますが、パフォーマンスと視覚品質のバランスが良好であると考えました。  

## <a name="try-it-out"></a>試してみましょう。 

HoloLens 2 を起動し、Microsoft Store からアプリを [ダウンロード](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) するか、GitHub から [リポジトリ](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) を複製して自分でアプリをビルドします。  

## <a name="about-the-team"></a>チームについて

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>ジャックキャロン</b><br><i>リードゲームデザイナー</i><br>Jack は、現在、HoloLens 2 プロジェクトや Altをはじめとする Microsoft の Mixed Reality エクスペリエンスで機能しており、以前は HoloLens プラットフォームチームのデザイナーでした。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>夏 Wu</b><br><i>Producer</i><br>夏は、mixed reality 開発者プラットフォームに勤務しており、チームのエンジン関連の作業には参加していません。</td>
</tr>
</table>

Kippy の脱出を実現するために、 [フレームストア](https://www.framestore.com/) で友人に感謝しています。 キャラクターの開発、資産の設計、ゲームプログラミングから、このプロジェクトのコラボレーションは非常に重要でした。  