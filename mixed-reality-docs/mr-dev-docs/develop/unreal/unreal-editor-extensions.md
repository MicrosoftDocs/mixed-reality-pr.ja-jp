---
title: Unreal のエディター拡張機能
description: カスタム スクリプト、スクリプト アクション、ユーティリティ ウィジェットを使用して Unreal Engine エディターを拡張する方法について説明します。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, エディター拡張機能, Unreal エディター, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584921"
---
# <a name="editor-extensions-in-unreal"></a>Unreal のエディター拡張機能

Unreal には、エンジンをニーズに合わせてカスタマイズできる広範な機能セットが用意されています。 簡単ですが限的的なものから、非常に強力ですが複雑なものまで、幅広い機能があります。 以下の手順は、複雑さが増す順になっています。 一般に、問題のより簡単な解決策を探し、そのオプションを使い果たしたら、より複雑なオプションに移行する必要があります。 例として、ほとんどの場合、プラグインの代わりに基本的なコンストラクション スクリプトを使用できます。 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>コンストラクション スクリプト

コンストラクション スクリプトを使用して、Blueprint インスタンスの作成時に実行される初期化アクションを実行できます。

* [ユーザー コンストラクション スクリプト](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [ブループリントの例](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [ビデオ チュートリアル](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>スクリプト アクション

スクリプト アクションは、Editor Utility Blueprint です。 Unreal エディターで次のようにしてそれを起動できます。
* コンテンツ ブラウザーで **[Assets]\(アセット\)** を右クリックします
* または、レベル ビューポートまたワールド アウトライナーで **[Actors]\(アクター\)** を右クリックします

スクリプト アクションは、アセットまたはアクターのセットについてのコンテキストをブループリントのロジックで認識する必要がある場合に、特に適しています。 通常、スクリプト アクションにより、アクションの実行時に選択したアセットまたはアクターのリストが取得され、それらのオブジェクトが変更されたり、グラフで考慮されたりします。

* [スクリプト アクション](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [プロジェクトの開始時にスクリプト アクションを実行する](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Editor Utility Widget

新しい UI 要素を追加して Unreal エディターのユーザー インターフェイス (UI) を変更したいときはいつでも、[Editor Utility Widget](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) を使用できます。 Editor Utility Widget は、Unreal Motion Graphics (UMG) に基づいているため、他の UMG Widget Blueprint の場合と同じように、ブループリントでウィジェットを設定できます。

これらのウィジェットはエディター UI 専用であり、カスタム エディターのタブを作成するために使用できます。 その後、既存のエディターのタブを選択するのと同様に、[Windows]\(ウィンドウ\) メニューからこれらのカスタム タブを選択できます。

## <a name="plugins"></a>プラグイン

Unreal を使用すると、UE4 のツールとランタイムで使用する独自のカスタム [プラグイン](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html)を開発して管理できます。 いつでも Unreal エディターでプラグインを有効または無効にすることができます。 プラグインを使用して、実行時のゲームプレイ機能を追加したり、エンジンの組み込み機能を変更したり、新しいファイルの種類を作成したり、エディターの機能を拡張したりできます。

<!-- ## Engine modifications -->

