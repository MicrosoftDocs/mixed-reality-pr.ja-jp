---
title: ハンド コーチ
description: 3D ハンドは、システムがユーザーの手を認識しない場合にトリガーされます。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、手作業、イマーシブヘッドセット、MRTK、ハンズオン、ハンズオン、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: d925f28b1d34b5a157e89fc0ea56a7b28fffbe8f
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702348"
---
# <a name="hand-coach"></a>ハンド コーチ
![例: 手動](images/HandCoach/MRTK_handCoach.jpg)<br>

ユーザーの手がシステムによって検出されなかった場合にトリガーされる、3D でモデル化されたハンドです。 これは、ジェスチャが学習されていないときにユーザーをガイドする "教職員" コンポーネントとして実装されます。 ユーザーが指定されたジェスチャをピリオドに対して実行していない場合、針は遅延でループします。 針を使用すると、ボタンを押すか、またはホログラムを選ぶことができます。  

## <a name="hand-coach-provided"></a>提供される手

現在の相互作用モデルは、スクロール、遠くの選択、およびニアタップなどのさまざまなジェスチャコントロールを表します。 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets">Mrtk</a>に用意されている既存のジェスチャの完全な一覧を次に示します。

:::row:::
    :::column:::
       ![Near Select の例](images/HandCoach/NearSelect.gif)<br>
       **Near Select の例: ボタンを選択する方法または対話型オブジェクトを閉じる方法**<br>
    :::column-end:::
    :::column:::
       ![エアタップの例](images/HandCoach/AirTap.gif)<br>
        **エアタップの例-遠く離れたオブジェクトを選択する方法を示すために使用されます。**<br>
    :::column-end:::
    :::column:::
       ![移動の例](images/HandCoach/Move.gif)<br>
       **スペースでのオブジェクトの移動の例-スペースでのホログラムの移動方法を示すために使用されます。**<br>
    :::column-end:::
    :::column:::
       ![回転の例](images/HandCoach/Rotate.gif)<br>
       **ホログラムまたはオブジェクトの回転方法を示す Rotate-Used の例**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![スケールの例](images/HandCoach/Scale.gif)<br>
       **拡大/縮小するホログラムの操作方法を示すために使用されるスケールの例**<br>
    :::column-end:::
    :::column:::
       ![パームアップの例](images/HandCoach/PalmUp.gif)<br>
        **パームアップの例–メニューを表示するために使用することをお勧めします。**<br>
    :::column-end:::
    :::column:::
       ![コードの切り替えの例](images/HandCoach/HandFlip.gif)<br>
       **手動フリップ-メニューを表示する別の方法**<br>
    :::column-end:::
    :::column:::
       ![スクロールの例](images/HandCoach/Scoll.gif)<br>
       **スクロールの例–リストまたは長いドキュメントをスクロールするために使用されます。**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>設計概念

Hololens2 については、instinctual と自然なジェスチャに基づいて手動で相互作用を設計しました。 これらは、ほとんどのユーザーにとって直観的であると考えられます。したがって、専用のジェスチャの学習時間は作成されませんでした。 代わりに、このようなジェスチャの詳細については、行き詰まっている可能性のあるユーザー、またはホログラムとの対話に慣れていないユーザーを支援するための手を作成しました。 学習に時間がかかりません。ユーザーに対して、ユーザーの操作を実行する方法が最適なオプションであることを示しています。 この調査では、ユーザーはジェスチャを調べることができましたが、少しのガイダンスが必要でした。 ユーザーが特定の期間にわたってオブジェクトと対話しないことを検出した場合は、正しい針と指の位置を示す針がトリガーされます。 

### <a name="intuitive"></a>にくい

ハンドをアニメーション化する場合は明らかで、混乱を招くことはありません。 実際のアニメーションは、その目的を理解するためにユーザーに呼び出すするジェスチャを表しています。 

たとえば、ユーザーがボタンを押すと、ボタンを押すという手がトリガーされます。

![例: 手動でタップする](images/HandCoach/NearSelect_unity.gif)<br>
*Gem の近くをタップしたときのデモ*  

### <a name="hand-scale"></a>手動スケール

UI メニューを使用してさまざまなサイズをテストしました。そのため、サイズが真だったとしても、menacing のように感じられますが、小さすぎるとジェスチャを確認して理解するのは困難でした。 

**ボイスオーバーとハンド**

ユーザーは、音声によって1つの命令セットをリッスンできないことを想定しています。 Sensory の過負荷を軽減するために、ユーザーが注目したり競争したりするのに役立つ手順を順番に説明します。


## <a name="can-i-create-my-own"></a>自分で作成できますか。

はい、ご利用いただけます。 ゲーム用に独自の独自のジェスチャを作成し、コミュニティに投稿することをお勧めします。
アプリに使用できる Rigged ハンドの Maya ファイルが提供されています。このファイルは、 <a href="files/HandCoach_MRTK.zip">HandCoach_MRTK.zip ダウンロード</a>できます。

![Maya でのアニメーションの例](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya のアニメーションの例*


**推奨 authoring tool**

3D アーティストの中では、多くの場合、 [Autodesk の Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) を使用します。これは、HoloLens を使用して、資産の作成方法を変革できます。 提供されるハンズオンファイルは Maya バイナリファイルであるため、Maya を使用してハンドをアニメーション化してエクスポートすることをお勧めします。 別の3D プログラムを使用する場合は、「」を参照 <b>してください。FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> HandCoachMRTK_FBX.zip をダウンロード </a> して、独自のコントローラー設定を作成します。 

提供されている maya ファイルをダウンロードして使用する場合は、unity を0.6 にスケールダウンすることをお勧めします。

![例: Maya の手動のリモートテストマシン群](images/HandCoach/MayaExample.png)<br>
*Rigged ハンド*

### <a name="technical-specs"></a>技術仕様

*   Maya Ascii 形式で使用できる2つのききファイル
*    左手のバイナリ形式では、Right および Left を使用できます。
*   Maya ファイルを 24 FPS に設定する
*   ファイル内には、2つのききまたはシングルききのジェスチャに使用できる左側と右側のハンドがあります。 右側は、既定でのみ表示されます。
*   フェードの最初と最後に約10フレームのバッファーを残しておくことをお勧めします。
*   指定したターゲットを使用してオブジェクトをアニメーション化する場合は、既定のボックスまたは Null にアニメーション化することをお勧めします。
*   ボックスなどの物理的なオブジェクトをアニメーション化する場合、そのベストプラクティスとして、Maya 内の平行移動はアニメーション化せず、Unity またはコードでアニメーション化することをお勧めします。
*   意味のある情報を伝達するには、表示されるアニメーションは1.5 秒でなければなりません
*   アニメーションに問題がなければ、次のようになります。
    *   すべてのジョイントおよび焼き付けるキーフレームを選択する
    *   コントローラーを削除し、ジョイントとメッシュを選択して、FBX としてエクスポートします。
    *  複数のアニメーションがある場合は、Maya の組み込みゲームエクスポーターを使用できます。 https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Maya からのエクスポート

アニメーションに問題がなければ
* すべての結合を選択: > 階層を選択します

     ![例: メニューの階層](images/HandCoach/Hierarchy.png)<br>
* アニメーションを焼き付けるする: アニメーションに切り替える > キー > 焼き付けるアニメーション

     ![例: 焼き付ける Animation Menu Location](images/HandCoach/BakeAnimation.png)<br>
* コントローラーのマシン: Outliner > MainR_Grp または MainL_Grp を削除します。

     ![例: コントローラーのリモートテストのメニューの場所](images/HandCoach/ControllerRig.png)<br>

* [FBX としてエクスポート]: 選択 JNT + メッシュ: ファイル > エクスポートの選択 (オプションボックス) > エクスポートの選択

     ![例: エクスポート選択メニューの場所](images/HandCoach/OptionBox.png)<br>

     ![例: メニューの場所](images/HandCoach/SelectionExport.png)<br>

     ![例: エクスポートオプションメニューの場所](images/HandCoach/FBXSelection.png)<br>


 FBX としてエクスポートし、Unity に導入する場合は、針を0.6 にスケーリングします。 これは、実際の表示に最適なバランスであることがわかりました。 

![例: Unity の設定](images/HandCoach/HandHintScale.png)<br>
*MRTK で HandCoach_R prefab の Unity 設定が見つかりました*


## <a name="implementing-hands-into-your-unity-project"></a>Unity プロジェクトにハンズオンを実装する

### <a name="best-practices"></a>ベスト プラクティス
*    Unity を0.6 にスケールダウンすることをお勧めします
*   針は2回再生され、完了していない場合はジェスチャが完了するまで連続してループされます。 ユーザーが登録してジェスチャを確認するまでの時間を確保するために、針を2回ループする必要があります。 ループの間で、ハンドインとフェードアウトを行う必要があります。 
 *  ユーザーの手が HL2 カメラによって表示されていても、ユーザーが必要な対話を行っていない場合は、10秒後にハンドが表示されます。
*   ユーザーの手が HL2 カメラによって表示されない場合は、5秒後に針が表示されます。  
*   アニメーションの途中でユーザーの手が HL2 カメラによって視覚的に追跡されている場合は、アニメーションが完了してフェードアウトします。
*   ボイスオーバーを含む場合は、ハンドのジェスチャに対応することをお勧めします。
*   少なくとも1回は、ユーザーがスタックしていることが検出された場合にのみ、ジェスチャを繰り返します。
*   特定の指と位置が重要である場合は、アニメーションの微妙な差異をユーザーがはっきりと確認できるようにします。 最も重要な部分が明確に表示されるように、角度を試してみてください。 
* 手にひずみがある場合は、Unity の品質設定にアクセスして、ボーンの量を増やす必要があります。 
 Unity の編集 > プロジェクトの設定 > 品質 > 他の > Blend の重みにアクセスします。 Smooth 関節を表示するには、"4 つの骨" が選択されていることを確認してください。 

   ![例: プロジェクトの設定ウィンドウ](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>避けるべきこと
* ハンドのサイズが大きすぎます
* ユーザーに近すぎるユーザーを配置する
* ハンズオンは、1回だけ学習する必要があります。 教育を超えると混乱を招き、messiness
*   Unity に取り込むには、最新の MRTK をこちらからダウンロードしてください。 https://github.com/microsoft/MixedRealityToolkit-Unity
    *   素材: Teaching_Hand2
    *   スクリプト: <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk</a>での mrtk のガイドラインを参照してください。
    *   プロジェクトごとの設定
        *   UWP に設定されたシーン: 命令は、「Windows Mixed Reality 用の [Unity プロジェクトの構成](../develop/unity/Configure-Unity-Project.md) 」にあります。

## <a name="see-also"></a>関連項目
* [相互作用-基本](interaction-fundamentals.md)
* [資産の作成プロセス](asset-creation-process.md)
* [ジェスチャ](../gestures.md)
* [ツールをインストールする](../develop/install-the-tools.md)
* [Unity プロジェクトの構成](../develop/unity/Configure-Unity-Project.md)
* [Unity 開発の概要](../develop/unity/unity-development-overview.md)
* [MRTK 101](../develop/unity/mrtk-101.md)
