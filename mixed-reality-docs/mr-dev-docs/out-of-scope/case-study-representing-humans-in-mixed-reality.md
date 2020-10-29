---
title: ケーススタディ-混合現実の人間を表す
description: すばらしい要素を作成できるだけでなく、混合現実の環境、オブジェクト、および人間の最も現実的なキャプチャを利用する場合、どのような種類の営業案件が浮上しますか。
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、人間、アバター、mixed reality capture、容量ビデオ
ms.openlocfilehash: 1a14759a6292a0fcc1e6fd36f518fff537c67dca
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687399"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>ケーススタディ-混合現実の人間を表す

ライトを使用した James Turrell 設計。 作業にステップインすると、1つの深さと焦点がわかります。 壁面は、接近と無限の両方に見えるので、影が付けられます。 ライトの色と拡散を慎重に調整することによって設計された未知の見識。 [Turrell は、このような sensations](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) を *"目で* 見ています" として説明します。これは、現実を理解するための1つの方法です。 1 Turrell imagines のようなすばらしい世界は、現在、mixed reality のイマーシブ環境とは異なり、このようにして、感知を利用するための強力なツールです。

![横長-James Turrell (1998)](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>複雑な現実世界環境を混在環境で表現するにはどうすればよいでしょうか。

Turrell の作業をイマーシブエクスペリエンスで表現することは、説得力のある課題になります。 照明、スケール、および空間オーディオには、彼の仕事を表す機会が存在します。 幾何学の幾何学的な周囲には比較的単純な3D モデリングが必要ですが、アーティストのフォーカスに対しては2番目になります。つまり、感知に対するライトの影響です。

Turrell の stark、minimalism は彼の仕事の特徴ですが、混合現実により複雑な資料を持つ展示を希望する場合はどうでしょうか。

![感嘆符-Ai Weiwei (2013)](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

2013では、アーティスト Ai Weiwei 公開は、ベニス Biennale で886アンティーク stools [を使用して、tangling 作品を](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) しています。 各木製腰掛けは、中国語職人気質が非常に重要であり、これらの stools が世代間で渡された時代 (年号) から来ています。 Stools 自体は、木の複雑さ、ピースの精度、慎重な配置など、現代の文化に関する Ai のコメントに不可欠です。

アンティーク stools は、アーティストのメッセージを信頼性の高い方法で配信します。 現実的な表現は、このエクスペリエンスにとって非常に重要であり、技術上の課題を作成することが重要です。つまり、Sculpting stools の各886は、非常に包括的で高価なものになります。 モデルと配置にはどのくらいの時間がかかりますか。 マテリアルの信頼性を維持するにはどうすればよいでしょうか。 これらのオブジェクトを最初から再作成すると、多くの点で、アートワーク自体の解釈が変わります。 アーティストの意図を維持するにはどうすればよいですか。

## <a name="methods-of-capturing-mixed-reality-assets"></a>Mixed reality 資産をキャプチャする方法

最初から何かを作成する代わりに、実際の処理をキャプチャします。 段階的な一連のキャプチャ方法を使用して、混合現実 (環境、オブジェクト、および人) で検出された各主要な資産の種類の認証済み表現を開発できます。

広範なカテゴリは、適切に確立された2D ビデオから最新の形式の容量ビデオまで多岐に分類されています。 Ai Weiwei の展示場の場合、スキャン (多くの場合、基本的な手法では photogrammetry) を使用して、展示場を作成し、各 stools をスキャンします。 360°写真とビデオキャプチャは、展示場全体に配置された高品質の双方向カメラを活用した経験を仮想化するためのもう1つの方法です。 これらの手法では、スケールの意味について理解を深め、理想的には各ピースの職人気質を確認するのに十分な詳細が得られます。 これらはすべて、既存のデジタル形式で、新しい vistas とパースペクティブを実現することができます。

![2D から容量へのビデオ](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

すばらしい要素を作成できるだけでなく、混合現実の環境、オブジェクト、および人間の最も現実的なキャプチャを利用する場合、どのような種類の営業案件が浮上しますか。 これらの方法の重複を調べると、メディアがどこに配置されているかを調査するのに役立ちます。

環境とオブジェクトの場合、360°のイメージングソフトウェアは photogrammetry の要素を含むように進化しています。 深度情報をシーンから分離することによって、高度な360°のビデオでは、仮想シーンを見ているときに fishbowl で頭が動かなくなるという感じを軽減できます。

モーションキャプチャとスキャンを組み合わせて拡張する新しいメソッドが新たに導入されました。モーションキャプチャは、視覚効果や画像に対して詳細な人間移動を行うための基本であり、スキャンにより、顔や手などの詳細な人の視覚エフェクトをキャプチャすることができます。 レンダリングテクノロジの進歩により、容量ビデオと呼ばれる新しいメソッドによってこれらの手法が構築され、ビジュアルと深度情報が組み合わされて、次世代の3D ヒューマンキャプチャが作成されます。

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>容量ビデオと、本物の人間によるキャプチャの追求

人間はストーリーテリングの中心となります。最もリテラルな意味では、人間の声、実行、またはストーリーの件名を意味します。 今日のイマーシブエクスペリエンスの中で最もイマーシブで目になるのは、ソーシャルです。 悪化の新しい環境で友人を見ていくために、生活室での mixed reality エクスペリエンスの共有を実現します。 人間の要素は、最もすばらしい現実でもあります。

![VR の Mindshow](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

イマーシブエクスペリエンスのアバターは、ストーリーテリングで新しい種類の具現化を有効にします。 最新のアプリは、仮想ボディの所有権の概念を再考と共に、人間との間の距離を排除する世代の飛躍を設定します。 [Mindshow](https://mindshow.com/)のような企業は、アバターを活用するクリエイティブツールを開発しています。これは、ユーザーがまったく新しいペルソナと文字を利用できるようにするためのものです。 他の人は、人間 [の](https://en.wikipedia.org/wiki/Uncanny_valley)ような属性の性質 (および必要な場合) を調べることができます。 今日、このリアリティがないことは、日常的な開発者にとっての技術的な問題のホストと共に、 [人間の likeness の](https://en.wikipedia.org/wiki/Uncanny_valley) 欠如を回避するのに役立ちます。 これらの理由 (およびその他) については、近い将来、現実的ではないアバターが既定のものになる可能性が非常に高くなります。 しかし、現実には、現実には mixed reality に大きな課題がありますが、 *3d 空間で人間を正規表現する必要がある主なシナリオがあり* ます。

Microsoft では、Microsoft Research からの小規模なチームが、容量ビデオの形式で人間をキャプチャする方法を開発してきました。 今日のプロセスはビデオ運用に似ています。 sculpted 資産に移動を適用するのではなく、完全な3D 記録です。 パフォーマンスとイメージはリアルタイムでキャプチャされます。アーティストの仕事ではなく、本物の表現です。 また、テクノロジは商用アプリケーションを拡張することから始まりますが、容量ビデオの影響は、 [マイクロソフトのパーソナルコンピューティングのビジョン](https://www.youtube.com/watch?v=tcyj-_IEWt8)に不可欠です。

![容量ビデオ SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

信頼性の高い人間によるキャプチャでは、複雑な現実のエクスペリエンスの新しい一意のカテゴリをロック解除します。 デジタルメディアでは、著名人、同僚、またはお好きな人がいるかどうかを確認することで、親密性を作成することができます。 彼らの顔、式、動きの中での微妙な部分は、だれがそのようなものであるかということです。 これらの人間の品質を3D 空間でキャプチャできるようになると、どのようなチャンスがありますか。

現在、チームは、エンターテインメントや教育などのセクターに焦点を当てることによって、容量ビデオの範囲をプッシュしています。 [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) は、 [有名人](https://www.youtube.com/watch?v=BwWueXlsOrA) のような現実のストーリーを作成します。 [宛先: Mars](https://www.jpl.nasa.gov/news/news.php?feature=6220)は、現在、NASA のケネディ宇宙センターで、伝説 astronaut の容量ビデオを特徴としています。 このエクスペリエンスにより、訪問者は、mars で人間の colonization を追求することによって、Mars の表面を説明できます。

## <a name="humans-are-fundamental-to-mixed-reality"></a>人間は mixed reality の基礎になります。

これらのビデオを作成する方法を設計することは困難であるように思えますが、1つはチームが大きな可能性を認識していることです。 また、テクノロジがよりアクセスしやすくなり、記録からリアルタイムのキャプチャに移動するため、これらの機会が拡張されます。

[Holoportation](https://www.microsoft.com/research/project/holoportation-3/) は、同じ基本テクノロジを基盤とする研究作業であり、視覚的および深度情報を authentically し、結果をリアルタイムで表示します。 チームでは、会話や共有エクスペリエンスの未来における現実的な人間表現の力を調べることにしています。 世界中のどこからでも3次元のキャプチャを環境に追加できるとどうなるでしょうか。

![メッセージ交換の未来](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

新しいレベルの immersion を Skype などの日常のアプリに重ねて、デジタル会議やビジネス旅行の概念を大幅に調整するために、容量ビデオでは、独自のシナリオが開かれています。これは、専門家の家やデジタル友人が、リビングルームの couches やいすに座っています。 Mixed reality エクスペリエンスに正規の人間表現を追加すると、デジタル会議とビジネス旅行の概念が大幅に変形します。

James Turrell の抽象図と Ai Weiwei の重要なリアリティによって、独自の技術的な課題が生じます。そのため、人間をクリエイティブなアバターや現実的なキャプチャとして表す方法を用意してください。 もう一方のライトでは無視することはできません。また、の可能性を調べることで、この新しいスペースでの人間との対話を理解するのに役立ちます。

## <a name="about-the-author"></a>著者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>マーク Vitazko</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>
