---
title: ケーススタディ-HoloLens 設計チームの最初の年
description: 2016年1月に HoloLens 設計チームに参加したときに、2D flatland から3D ワールドへの旅が開始されました。
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、design、刊行物、個人用
ms.openlocfilehash: 3c6444094663498ef4b253df6ed8dd7e82cc8319
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687407"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>ケーススタディ-HoloLens 設計チームの最初の年

2016年1月に HoloLens 設計チームに参加したときに、2D flatland から3D ワールドへの旅が開始されました。 チームに参加する前に、3D デザインの経験はほとんどありませんでした。 これは、1つのステップから始まる1000マイルの旅に関する中国語 proverb に似ていました。ただし、最初の手順はうるうでした。

![2D から3D への移行](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*2D から3D への移行*

> *「車を運転する方法を知らなくても、運転席に座りました。私は怖いていましたが、非常に焦点を絞っています。」*<br>
> — Hae Jin Lee

過去1年間、スキルと知識をできるだけ早く取得しましたが、まだ学んでいます。 ここでは、2D から3D への相互作用デザイナーからの移行に関するビデオチュートリアルを使用して、4つの観測を作成しました。 私の経験により、他の設計者が3D に移行してくれることを願っています。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>適正なフレーム。 Hello 空間/diegetic UI

ポスター、雑誌、web サイト、またはアプリの画面をデザインしたときには、定義済みのフレーム (通常は四角形) はすべての問題にとって定数でした。 HoloLens またはその他の VR デバイスでこの投稿を読んでいない場合は、フレーム内で安全に保護された2D 画面を通じて *、外部からこれを参照* しています。 コンテンツは外部にあります。 ただし、Mixed Reality ヘッドセットでは *フレームが* 削除されるため、コンテンツスペース内では、コンテンツを検索して内部から検索することができます。

これは概念的に理解しましたが、最初に2D の考え方を3D 空間に転送するのは間違いでした。 これは明らかにうまくいきませんでした。これは、3D 空間には、(ユーザーのヘッド移動に基づいた) ビューの変更などの独自の固有のプロパティがあり、 [ユーザーが快適に](https://www.youtube.com/watch?v=-606oZKLa_s/) 使用するための要件 (デバイスのプロパティとそれらを使用している人間に基づく) が異なるためです。 たとえば、2D UI デザイン領域では、画面の隅に UI 要素をロックするのは非常に一般的なパターンですが、この HUD (ヘッドアップディスプレイ) スタイルの UI は MR/VR エクスペリエンスで自然には感じません。ユーザーの immersion の妨げになるため、ユーザーの不快感が発生します。 これは、起きのように見えにくい埃がメガネにあるようなものです。 時間の経過と共に、3D 空間にコンテンツを配置し、本文ロックの動作を追加して、コンテンツが相対的な固定距離でユーザーに続くようにすることを学習しました。

![本文-ロック済み](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*本文-ロック済み*

<br>

![世界ロック](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*世界ロック*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>フラグメント: 優れた Diegetic UI の例

たとえば、 [Asobo Studio](https://www.asobostudio.com/) for HoloLens によって開発された最初のユーザー犯罪 thriller[は、優れ](https://www.microsoft.com/p/fragments/9nblggh5ggm8)た Diegetic UI を示しています。 このゲームでは、ユーザーが主な文字になります。これは、謎の解決を試みる検出です。 この謎を解決するための重要な手がかりは、ユーザーの物理的な部屋で sprinkled を獲得し、多くの場合、既存のものではなく架空のオブジェクトに埋め込まれることです。 この diegetic UI は、本文でロックされている UI よりも検出できない傾向があります。そのため、Asobo チーム巧妙では、仮想文字の、サウンド、ライト、ガイドなどの多くの手掛かりを使用しています (ヒントの場所を示す矢印など)。

![フラグメント-Diegetic UI の例](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*フラグメント-Diegetic UI の例*

### <a name="observations-about-diegetic-ui"></a>Diegetic UI についての所見

空間 UI (本文ロックとワールドロックの両方) と diegetic UI には、独自の長所と短所があります。 デザイナーは、可能な限り多くの MR/VR アプリを試し、さまざまな UI 配置方法について独自の理解と sensibility を開発することをお勧めします。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism と対話式の戻り値

現実世界のオブジェクトの形を模倣したデジタルインターフェイスは、設計業界では過去 5 ~ 7 年間 "uncool" になっています。 Apple が iOS 7 でフラット設計を行うことにした場合、Skeuomorphism が、最終的にはインターフェイスの設計方法として死んだと思われます。 しかし、新しい medium, MR/VR ヘッドセットが市場に到着し、Skeuomorphism のように再び返されるように見えます。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>ジョブシミュレーター: skeuomorphic VR デザインの例

[ジョブシミュレーター](https://jobsimulatorgame.com/)は、 [Owlchemy Labs](https://owlchemylabs.com/) によって開発された whimsical ゲームであり、skeuomorphic VR の設計の最も一般的な例の1つです。 このゲームでは、ロボットが人間や人間を置き換えるために、"Auto 整備士"、"グルメ Chef"、"Store クラーク"、または "Office Worker" という4つの異なるジョブのいずれかで、日常的なタスクを実行するために必要なものを体験しています。

Skeuomorphism の利点は明確です。 このゲーム内の使い慣れた環境とオブジェクトを使用すると、新しい VR ユーザーの操作性が向上し、仮想空間に存在することになります。 また、使い慣れた知識と動作をオブジェクトとそれに対応する物理的反応に関連付けることによって、管理されているように感じられます。 たとえば、コーヒーをコーヒーに移動するには、単にコーヒーのコンピューターに移動し、ボタンを押して、カップハンドルをつかんで、実際の世界でのように、口に傾ける必要があります。

![ジョブシミュレーター](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*ジョブシミュレーター*

MR/VR はまだ開発中であるため、説明 MR/VR テクノロジを使用して世界中のより多くのユーザーに導入するには、特定の程度の skeuomorphism を使用する必要があります。 また、skeuomorphism またはリアルな表現を使用すると、手術やフライトシミュレーションなどの特定の種類のアプリケーションにとって有益な場合があります。 これらのアプリの目的は、実際の世界に直接適用できる特定のスキルを開発して調整することであるため、実際のシミュレーションの方が、より多くの知識が得られます。

Skeuomorphism は1つのアプローチにすぎないことに注意してください。 MR/VR 世界の可能性ははるかに高く、設計者は、"MR/VR" で一意に可能な新しい affordances という、魔法のあるハイパー自然な相互作用を作成する必要があります。 最初に、通常のオブジェクトに魔法の累乗を追加して、ユーザーが自分の基本的な要望 (たとえば、omniscience と、) を達成できるようにすることを検討してください。

![Doraemon の魔法のドア (左) と Ruby slippers (right)](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon の魔法のドア (左) と ruby slippers (right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>VR での skeuomorphism に関する観測

Harry ポッターでは、Oz のウィザードの "Doraemon" の "Ruby Slippers" から "Maurader's map" まで、通常のオブジェクトの例として、一般的な架空の魔法を持つ通常のオブジェクトの例があります。 これらの魔法のオブジェクトを使用すると、現実世界とすばらしいものとの間の接続を視覚化できます。 このオブジェクトを設計する場合は、機能とエンターテインメントのバランスを取る必要があることに注意してください。 分野のために、純粋に魔法のようなものを作成することは注意してください。

## <a name="understanding-different-input-methods"></a>さまざまな入力方法を理解する

2D メディア向けに設計された場合は、タッチ、マウス、キーボードによる入力のやり取りに焦点を当てる必要がありました。 MR/VR デザイン領域では、本文がインターフェイスになり、ユーザーはより直感的で仮想オブジェクトと直接接続できる、音声、宝石、ジェスチャ、 [6 自由型コントローラー](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)、グローブなどの幅広い入力方法を使用できます。

![HoloLens で使用可能な入力](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*HoloLens で使用可能な入力*

> *"すべてのものに最適です。他のものには最悪です。"*<br>
> - [請求書](https://www.billbuxton.com/)

たとえば、HMD デバイスでのベアハンドとカメラセンサーを使用したジェスチャ入力では、コントローラーまたは装着された sweaty グローブからユーザーを解放しますが、頻繁に使用すると物理的な疲労 (gorilla arm) が発生する可能性があります。 また、ユーザーは、目を見たままにしておく必要があります。カメラに手が表示されない場合は、手を使用できません。

音声入力は複雑なタスクを走査する場合に適しています。これは、ユーザーが1つのコマンドで入れ子になったメニューを使用できるようにするためです (たとえば、"Laika studio によって作成されたムービーを表示する" など)。 ただし、音声入力は、ノイズの多い環境ではうまく機能しない場合や、非常に非表示領域に適していない場合があります。

ジェスチャと音声に加えて、手にかけられた追跡コントローラー (たとえば、Oculus touch、Naopak など) は、使いやすく、正確で、ユーザーの [proprioception](https://en.wikipedia.org/wiki/Proprioception)を活用し、パッシブな haptic キューを提供するため、非常に一般的な入力方法です。ただし、これらの利点は、ベアハンドで完全な指追跡を使用できないという代償を伴います。

![Senso (左) と Manus VR (Right)](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (左) と Manus VR (Right)*

一般に、手袋は、MR/VR の波のおかげで、もう一度支持されています。 最近では、脳/マインドの入力を始めて、EEG または EMG センサーをヘッドセット ( [MINDMAZE VR](https://www.mindmaze.com/)など) に統合することによって、仮想環境のインターフェイスとして牽引力を獲得しました。

### <a name="observations-about-input-methods"></a>入力方式に関する観測

これらは、MR/VR の市場で利用可能な入力デバイスのサンプルにすぎません。 これらは、業界が成熟し、ベストプラクティスに同意するまで継続的に続きます。 それまでは、デザイナーは新しい入力デバイスを認識し、特定のプロジェクトの特定の入力方法に精通している必要があります。 設計者は、制限の中でクリエイティブなソリューションを探す必要があります。また、デバイスの強みも試してみてください。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>ヘッドセットでシーンとテストをスケッチする

2D で作業したときは、ほとんどがコンテンツのみをスケッチしました。 ただし、それほど十分ではない mixed reality 領域では、 ユーザーと仮想オブジェクト間の関係をよりよく想像するために、シーン全体をスケッチする必要がありました。 私は、空間的な考え方を支援するために、 [映画 4d](https://www.maxon.net/en/products/cinema-4d/overview/) でシーンをスケッチし、 [Maya](https://www.autodesk.com/products/maya/overview/)でプロトタイプ作成用の単純なアセットを作成することがありました。 HoloLens チームに参加する前にプログラムを使用したことがなく、まだ newbie になっていますが、これらの3D プログラムを操作すると、 [シェーダー](https://en.wikipedia.org/wiki/Shader) や [IK (逆のキネマティック)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)などの新しい用語を使い始めることができました。

**「3D でシーンをどの程度正確にスケッチアウトしたかにかかわらず、ヘッドセットの実際のエクスペリエンスは、スケッチとほぼ同じではありませんでした。そのため、ターゲットヘッドセットのシーンをテストすることが重要です。 "— Hae Jin Lee**

HoloLens のプロトタイプを使用する場合は、「 [Mixed Reality チュートリアル](../develop/unity/tutorials.md) 」ですべてのチュートリアルを開始してみてください。 次に、Microsoft が開発者に提供する [HoloToolkit](https://github.com/Microsoft/HoloToolkit-Unity/) を使用して、holographic アプリケーションの開発を促進します。 何か行き詰まったときに、私は [HoloLens の質問 & 回答フォーラム](https://forums.hololens.com/categories/questions-and-answers/)に質問を投稿しました。

HoloLens のプロトタイプ作成に関する基本的な知識を取得した後、他の非占めるのプロトタイプを独自に強化する必要がありました。 ここでは、HoloLens を使用して単純な実行可能タイルを開発する方法を説明するビデオチュートリアルを作成しました。 基本的な概念について簡単に説明します。 HoloLens 開発の経験がゼロであっても、次のことを行うことができます。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*私は、私のようなプログラマ以外にも、この簡単なチュートリアルを行っていました。*

VR プロトタイプ作成では、 [Vr Dev School](https://learn.vrdev.school/) でコースを行ったので、Lynda.com で [仮想現実向けに3D コンテンツを作成](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) しました。 「VR Dev school」では、コーディングに関する知識をさらに詳しく説明しました。 Lynda コースでは、VR 用のアセットを作成するための簡単な概要を紹介しました。

## <a name="take-the-leap"></a>Leap を取る

1年前には、このようなことは少しでもあります。 これで、100% の労力が費やされたことがわかります。 MR/VR は依然として非常に若い中であり、多くの興味深い可能性があります。 将来の設計において、1つの小さな部分を再生できるようになりました。 3D 空間への旅にご協力いただければ幸いです。

## <a name="about-the-author"></a>著者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

 
