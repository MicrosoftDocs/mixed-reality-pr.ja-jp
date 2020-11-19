---
title: Maquette について
description: Maquette とその機能について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、プロトタイプ、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935531"
---
# <a name="about-maquette"></a>Maquette について

<!-- TODO(Harrison): Need consolidated logo with text -->
![ロゴ ](../images/MaquetteIcon.png) MaquetteScript の概要

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
Maquette は、標準 ECMA 5.1 Javascript を統合することにより、Maquette シーンとオブジェクトでの対話機能の投資を可能にします。これは VSCode 内から編集および実行できます。 オブジェクトのプロパティは、スクリプト内からの読み取りと設定、と呼ばれるオブジェクトメソッド、およびオブジェクトとシステムイベントに対して公開されます。 スクリプトは、スクリプトを介してアクセスできるシステムオブジェクトを使用して、Maquette 自体と対話することもできます。 ユーザーが対話できるさまざまな UI コントロールは、システムの一部です。 これらは、Maquette での作成時に追加することも、スクリプト内から作成および管理することもできます。 これらの要素を使用したユーザー操作イベント (データ入力、クリックなど) は、イベントとしてスクリプトにも公開されます。 これらの追加機能を使用すると、実験からデータ可視化まで、混合現実ユーザーシナリオを探索、AR または VR で完全に実現されたエクスペリエンスまで、単純な複雑なシーンを構築できます。

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
60の同一ビデオ
* エントリのタイトルカード
  * Maquette での対話型混合現実コンテンツの作成
  * スクリプト/対話機能/UI システム
* チームまたはビデオのキャプションによる VO の歓迎  説明
  * interactive MR コンテンツの作成を可能にするためのスクリプトの基礎
  * 非常に広範なブラシストロークでの使用方法について触れます
* スクリプト vingette の動作
  * [作成中] ダイアログボックス
  * アウトラインからのアプリの作成 (料理アプリのデモ)
  * Photogrammetry モデルでの構成
  * トラブルシューティングガイドとの対話
  * VSCode でのデバッグスクリプトの画面ビュー
  * シーン内のオブジェクトからスクリプトへのアクセスを取得する
  * その他...
* 終了時のタイトルのタイトルカード
  * Maquette へのリンク
  * スクリプトの使用を開始するには
  * お知らせ/ステータス/コミュニティ
  * 実行できる内容 (?) を確認してください。
  * フィードバックと、お役に立ち上げる方法

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [はじめに](installation.md)
* [例とサンプルアプリ](../samples/overview.md)
* [サポート](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a>フィードバックの送信

お客様のエクスペリエンスと結果についてご意見をお待ちしております。 フィードバック、提案、バグレポートは常に歓迎します。
リンクを <>