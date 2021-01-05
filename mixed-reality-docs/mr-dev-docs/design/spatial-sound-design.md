---
title: 混合現実アプリケーションでの空間サウンドの使用
description: 空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計のための強力なツールです。
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality、空間サウンド、設計、スタイル、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ジェスチャ、相互作用、減衰
ms.openlocfilehash: fe77d62bcdfc67579deee619fc7f4949676aaed6
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848177"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Mixed reality アプリケーションでサウンドを使用する方法

サウンドを使用して、ユーザーのアプリケーション状態のメンタルモデルを通知し、補強することができます。 必要に応じて spatialization を使用して、mixed reality の世界にサウンドを配置します。 この方法で聴覚とビジュアルを接続すると、相互作用の直感的な性質が高まり、ユーザーの信頼度が向上します。
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>サウンドを追加するタイミング

混合現実のアプリケーションでは、tactile インターフェイスがないため、多くの場合、2D アプリよりもサウンドが必要になります。 ユーザーに通知したり、対話を補強したりするときに、サウンドを追加します。

### <a name="inform-and-reinforce"></a>通知と補強

* 通知など、ユーザーによって開始されていないイベントについては、音を使用して、変更が発生したことをユーザーに通知します。
* 相互作用には複数の段階があります。 音を使用してステージの遷移を補強します。

相互作用、イベント、および推奨されるサウンド特性の次の例を参照してください。

### <a name="exercise-restraint"></a>演習ガイド

オーディオ情報の容量に制限はありません。
* 各サウンドは、特定の重要な情報を伝達します。
* アプリがサウンドを再生してユーザーに通知するときに、他のサウンドの音量を一時的に下げます。
* ボタンをポイントしたときのサウンド (次の情報を参照) については、待ち時間を追加して、音が過剰にトリガーされないようにします。

### <a name="dont-rely-solely-on-sounds"></a>サウンドだけに依存しない

よく使用されるサウンドは、ユーザーにとって価値があります。 ただし、サウンドがオフになっている場合でもアプリケーションが使用可能であることを確認してください。
* ユーザーの聴覚が不自由になっている可能性があります。
* アプリケーションは、大いな環境で使用できます。
* ユーザーには、プライバシーに関する考慮事項や、デバイスオーディオを無効にするその他の理由が考えられます。

## <a name="how-to-sonify-interactions"></a>相互作用を sonify する方法

混合現実の対話型には、ジェスチャ、直接操作、音声などがあります。 次の推奨される特性を使用して、これらのインタラクションのサウンドを選択または設計します。

### <a name="gesture-interactions"></a>ジェスチャの相互作用

Mixed reality では、ユーザーはマウスを使用してボタンを操作できます。 ボタンの操作は、通常、ユーザーがボタンをクリックするのではなく、ユーザーが操作をキャンセルできるようにしたときに発生します。 サウンドを使用して、これらのステージを補強します。 離れた場所にあるボタンをユーザーがターゲットとして使用できるようにするには、ポインターをポイントするサウンドの使用も検討してください。
* ボタン-enter キーを押すと、tactile の "クリック" が短くなります。<br/>例: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* ボタン-"押されていない" サウンドは、同様の tactile 感を持つ必要があります。 押されたサウンドよりも高いピッチで、完了の意味がわかります。<br/>例: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* ホバーサウンドの場合は、低周波数の thud やバンプなど、微妙で脅威のないサウンドを使用することを検討してください。

### <a name="direct-manipulation"></a>直接操作

HoloLens 2 では、独自の追跡はユーザーインターフェイス要素の直接操作をサポートしています。 他の物理的なフィードバックがない場合は、音が重要になります。

キーストロークの一番下に到達したときにユーザーが何も表示しないため、 *ボタンを押す* 音が重要になります。 キー移動のサウンドインジケーターは、小、軽度、occluded にすることができます。 ジェスチャの対話と同様に、ボタンを押すと、クリックのような短い tactile サウンドが表示されます。 Unpresses は、同じようなクリック音を持つ必要がありますが、ピッチが発生します。
* 例: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 例: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

グラブまたはリリースアクションを視覚的に確認することは困難です。 多くの場合、ユーザーの手は視覚的な効果を持つようになります。また、ハードハンドのオブジェクトには、"グラブ" という実際の視覚アナログがありません。 サウンドは、成功したグラブとリリースの相互作用を効果的に伝えることができます。
* グラブアクションには、オブジェクトの周りを閉じるように求めるための短い muffled tactile サウンドが必要です。 また、"whoosh" 音が発生して、手の動きを知らせる音が出てくることもあります。<br/>例: [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* リリースアクションは、同様の短いサウンドと tactile サウンドを取得する必要があります。 通常は、グラブ音と逆の順序で、オブジェクトが所定の位置にあることを通知する "whoosh" に影響を与えます。<br/>例: [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*描画* の相互作用は、ユーザーの手の動きによって決定された音量を持つ、固定のループサウンドを取得する必要があります。 ユーザーの手が、すぐに手を移動するときには、静かである必要があります。

### <a name="voice-interactions"></a>音声操作

音声のやり取りには、微妙な視覚要素があることがよくあります。 音を使用して、対話段階を補強します。 より多くの色調音を使用して、ジェスチャや直接操作サウンドと区別することができます。

* 音声コマンドの確認には、正の音を *使用します*。 増加している色調と主な音楽の間隔は効果的です。
* 音声コマンドの *エラー* には、より短い、正の音で聞こえない音を使用します。 負の音は避けてください。 代わりに、percussive のニュートラルサウンドを使用して、アプリケーションが相互作用から移動していることを通知します。
* アプリケーションにウェイクワードが含まれている場合は、デバイスが *リッスンを開始* するときに、短時間で緩やかに使用します。 アプリケーション *が* リッスンしている間に、微妙なループサウンドを使用します。

### <a name="notifications"></a>通知

通知は、アプリケーションの状態の変化や、ユーザーが開始しなかったその他のイベントを通知します。 状態の変更には、プロセスの完了、メッセージ、および電話の呼び出しを含めることができます。

Mixed reality では、オブジェクトがユーザーのビューのフィールドから移動する場合があります。 オブジェクトの種類と動き速度に依存する spatialized サウンドで、移動する *アニメーションオブジェクト* をペアにします。
* これは、アニメーションの最後に spatialized サウンドを再生して、オブジェクトの新しい位置をユーザーに通知するのに役立ちます。
* 段階的な移動では、移動中の "whoosh" サウンドを使用して、ユーザーがオブジェクトを追跡できます。

*メッセージ通知* 音は繰り返し発生する可能性があります。連続している場合もあります。 非常に重要なことです。 中間範囲の正の色調音が有効になります。

* 着信音の音声は、携帯電話の着信音と同様の品質を持つ必要があります。 これらのサウンドは、ユーザーが通話に応答するまで再生されるミュージックフレーズをループします。
* 音声通信の接続と切断には、短時間の色調音が必要です。 接続が成功したことを示すには、接続サウンドが正の音である必要があります。 切断音は、呼び出しの完了を示すニュートラルサウンドである必要があります。

## <a name="handle-spatialization"></a>Spatialization の処理

Spatialization は、ステレオヘッドホンまたはスピーカーを使用して、mixed reality の世界にサウンドを置きます。

### <a name="which-sounds-to-spatialize"></a>Spatialize する音

空間位置を持つイベントに関連付けられている場合は、サウンドを spatialized する必要があります。 これには、UI、埋めを行う AI 音声、および視覚的インジケーターが含まれます。

Spatialize *ユーザーインターフェイス* の要素を使用して、ユーザーの sonic "space" をまとめします。これは、ユーザーが聞く音声音の数を制限することによって行います。 オーディオフィードバックが spatialized されると、タッチ、グラブ、解放などの操作の相互作用がより自然になります。 これらの要素の距離の減衰に関する次の情報を考慮してください。

*視覚インジケーター* *を Spatialize し、表示* されていないときにユーザーにわかりやすく表示します。
    
これに対して、spatialization の *FACELESS AI 音声* や、空間位置が明確に定義されていないその他の要素については避けてください。 関連するビジュアル要素のない Spatialization は、ユーザーが見つけられない視覚的な要素があると考えることができないようにします。

Spatialization には、いくつかの CPU コストが伴います。 多くのアプリケーションは同時に最大で2つのサウンドを再生しています。 この場合、spatialization のコストはごくわずかです。 MRTK のフレームレートモニターを使用して、spatialization を追加した場合の影響を判断できます。

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>距離ベースの減衰を適用するタイミングと方法

物理的な世界では、遠く離れている音はより静かです。 オーディオエンジンは、ソースの距離に基づいてこの減衰をモデル化できます。 関連情報を通信するときは、距離ベースの減衰を使用します。

*視覚的なインジケーター*、アニメーション化された *ホログラム*、およびその他の情報音への距離は、ユーザーに関連します。 距離ベースの減衰を使用して、手掛かりを直感的に提供します。

各ソースの減衰曲線を、mixed reality ワールドの空間のサイズに合わせて調整します。 オーディオエンジンの既定の曲線は、多くの場合、大規模な (最大ハーフ kilometer の) スペースを想定しています。

ボタンアクションとその他の対話 *の段階的な段階* を補強する音は、減衰が適用されないようにします。 これらのサウンドの強化された効果は、ボタンへの距離を伝えるよりも重要です。 多くのボタンをクリックすると連続して表示される場合もありますが、特にキーボードでは混乱が生じる可能性があります。

### <a name="which-spatialization-technology-to-use"></a>使用する spatialization テクノロジ

ヘッドホンまたは HoloLens スピーカーでは、head 関連の転送関数 (HRTF) ベースの spatialization テクノロジを使用します。 これらのテクノロジは、物理的な世界でのヘッドの周りにおけるサウンド伝達をモデル化します。 サウンドソースが1のヘッドの向こう側にある場合でも、サウンドは減衰と遅延によって遠くの耳に伝達されます。 スピーカーパンは減衰にのみ依存し、サウンドが右側にあるときは左の耳に合計の減衰を適用し、もう1つの方法を適用します。 この手法は、"通常の聴覚" リスナーでは不快になる可能性があり、1つの耳で聴覚に障害があるリスナーではアクセスできません。

## <a name="next-steps"></a>次のステップ

* [Unity で空間サウンドを使用する](../develop/unity/spatial-sound-in-unity.md)
* [Roboraid のケーススタディ](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour のケーススタディ](case-study-spatial-sound-design-for-holotour.md)
