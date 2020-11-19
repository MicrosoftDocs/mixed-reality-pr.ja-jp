---
title: コア言語
description: Maquette のコア言語の詳細について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、プロトタイプ、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935539"
---
# <a name="maquettescript-core-language-details"></a>MaquetteScript コア言語の詳細

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette ロゴ ](../images/MaquetteIcon.png) MaquetteScript Core 言語の詳細

## <a name="accessing-maquette-object-and-namespace"></a>`Maquette`オブジェクトと名前空間へのアクセス

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette は、オブジェクトとその子を使用して、JavaScript の内部オブジェクトとインターフェイスを公開 `Maquette` します。 この機能については、 [Maquette オブジェクトと名前空間](https://www.maquette.ms/doc_staging/objects/Maquette.html) のドキュメントを参照してください。 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
`Maquette`オブジェクトには、Maquette 自体との対話を容易にし、繰り返し発生する問題を解決しやすくする最上位レベルの関数があります。 詳細については、 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)のドキュメントを参照してください。

## <a name="maquette-startup-and-loading"></a>Maquette のスタートアップと読み込み

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette は、特定の JavaScript ファイルを読み込んで評価し、次のタイミングで構成、セットアップ、および初期化を有効にします。

Maquette の起動時:
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

プロジェクトが読み込まれるたびに、次のようになります。
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

プロジェクトは、それぞれのプロジェクトスクリプトを読み込みます。
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript の実装

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Maquette で使用される JavaScript インタープリターは、 [Jint](https://github.com/sebastienros/jint)に基づいています。 Jint は ECMAScript 5.1 と互換性があり、 [ecmascript 6 からの追加の拡張機能](https://github.com/sebastienros/jint/issues/343)をサポートしています。 

この拡張機能 `.mqjs` は、Maquette javascript ファイルを通常の javascript と区別するために使用されます。

## <a name="see-also"></a>関連項目 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->