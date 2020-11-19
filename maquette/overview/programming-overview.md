---
title: プログラミングの概要
description: スクリプトを使用して Maquette オブジェクトおよびインターフェイスにアクセスする方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、プロトタイプ、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935509"
---
# <a name="programming-overview"></a>プログラミングの概要

<!-- TODO(Harrison): Need consolidated logo with text -->

![ロゴ](../images/MaquetteIcon.png) プログラミングの概要

Microsoft Maquette は、 [Jint](https://github.com/sebastienros/jint) インタープリターに基づく JavaScript (拡張機能付き ECMAScript 5.1) を使用します。 この拡張機能 `.mqjs` は、Maquette javascript ファイルを通常の javascript と区別するために使用されます。

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Maquette オブジェクトとインターフェイスは、オブジェクトを介してアクセスおよびスクリプト化でき `Maquette` ます。 Maquette のオブジェクトとインターフェイスに関するドキュメントは、Maquette の API リファレンスで提供されています。

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript は新たに追加され、流束になるため、変更が必要になります。 より詳細なドキュメントと更新プログラムがまもなく利用可能になります。

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>スクリプトのスポットライト

* サンプル/チュートリアルとして焦点を絞ったスクリプトのスポットライト
  * 2倍のイメージ/キャプション–スポットライトページへのリンク

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>MaquetteScript の概要

* Mqjs と JS
* プログラミング モデル
  * 編集と実行
* プログラミングワークフローへのリンク
* 結果を共有するためのリンク

## <a name="programming-workflow"></a>プログラミングワークフロー

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* スクリプト作成操作
* デバッガーの操作
* デバッグループ
* コードをコピー/貼り付けますか?

## <a name="running-mqjs-scripts"></a>Mqjs スクリプトの実行

<!-- TODO(Stefan): Need screenshot -->
MaquetteScript ファイルを実行するには、Maquette のコンパニオンウィンドウに移動し、[スクリプト] タブを開いて、スクリプトを検索します。

> [!NOTE] 
> スクリプトを出荷していないため、一部のオプションはまだ機能しません。

## <a name="vscode-editor-workflow"></a>VSCode エディターのワークフロー

VSCode 内から Maquette でスクリプトを評価するには、ユーザーは2つのコマンドを知る必要があります。

   `CTRL-5` 選択されたテキストまたはカーソルがある行全体を評価します。 

   `CTRL-SHIFT-5` ファイル全体を評価します。

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
テキストは Maquette に送信され、JavaScript 環境で評価されます。結果は VSCode の出力コンソールに返されます。 これは REPL (read-eval-print-loop) として使用できます。

## <a name="example-first-step"></a>最初の手順の例

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
VSCode で次のコードをファイルにコピーします。

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
コードまたはセクションだけを選択し、[実行] にヒットし `CTRL-5` ます。 これにより、キューブが作成され、前面に配置され、その色が変更されます。

拡張機能を使用して検索する例は他にもあります。

## <a name="sharing-results"></a>結果の共有

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
ユーザー/チーム間で共有する方法
* ドキュメントディレクトリの Zip プロジェクト
* プロジェクトをファイル共有にコピー
* チーム共有のファイルの場所を Maquette チームに追加しています

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* インクルード、相対/絶対パスを使用した他の場所のコードの参照、モジュール
* ライブラリ?
* ランタイム サポート
* 未解決の外部処理-エントリが見つからないか、クラッシュしたときの動作
* 特定のオブジェクトに関連付けられているスクリプトを追加/編集/観察することはできますか。
  * このスクリプトを他の場所にコピーして貼り付けることはできますか。
  * オブジェクトのプロパティについて
  * シーン内のオブジェクトに名前を付ける (スクリプトの名前を変更します)
  * オブジェクトに関連付けられているスクリプトの THIS または SELF キーワード
  * オブジェクトを右クリックすると、関連付けられているコード (およびそのすべての階層) が表示されます。
  * UI で選択し、VSCode のコードで起動できますか。
  * スクリプトソースファイル内のオブジェクトに関連付けられているコードを保持しますか?
  * クリックしたときに、プロパティウィンドウをオブジェクトの上に移動しますか? VR および [メイン] タブでは、
* セキュリティの問題
* テスト–未定の可能性がありますが、スクリプトでビデオまたはフレームの取得を提案できます
* バグ報告メカニズムを持っている場合は、他のユーザーのためにスクリプトを使用してアクセスできるようにすることができます (?)...あとで
* 展開–結果を "共有" する方法、実行可能ファイルとしてパッケージ
* デモの実行/制御 spectating/監視
* プレーヤーモード
* 共有用に "コンポーネント" を作成する方法についてのセグメントがあるかもしれません。 (未定)
  * #Include がありますか? これは純粋な JS を処理しますが、名前空間の競合が発生する可能性があります。
  * Maquette が、名前付きオブジェクトを使用して他の maquette を組み込み、JS コードに一致させることはできますか。
