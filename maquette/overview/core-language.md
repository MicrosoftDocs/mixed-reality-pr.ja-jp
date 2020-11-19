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
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="c69cd-104">MaquetteScript コア言語の詳細</span><span class="sxs-lookup"><span data-stu-id="c69cd-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="c69cd-105">![Maquette ロゴ ](../images/MaquetteIcon.png) MaquetteScript Core 言語の詳細</span><span class="sxs-lookup"><span data-stu-id="c69cd-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="c69cd-106">`Maquette`オブジェクトと名前空間へのアクセス</span><span class="sxs-lookup"><span data-stu-id="c69cd-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="c69cd-107">Maquette は、オブジェクトとその子を使用して、JavaScript の内部オブジェクトとインターフェイスを公開 `Maquette` します。</span><span class="sxs-lookup"><span data-stu-id="c69cd-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="c69cd-108">この機能については、 [Maquette オブジェクトと名前空間](https://www.maquette.ms/doc_staging/objects/Maquette.html) のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c69cd-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="c69cd-109">`Maquette`オブジェクトには、Maquette 自体との対話を容易にし、繰り返し発生する問題を解決しやすくする最上位レベルの関数があります。</span><span class="sxs-lookup"><span data-stu-id="c69cd-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="c69cd-110">詳細については、 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c69cd-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="c69cd-111">Maquette のスタートアップと読み込み</span><span class="sxs-lookup"><span data-stu-id="c69cd-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="c69cd-112">Maquette は、特定の JavaScript ファイルを読み込んで評価し、次のタイミングで構成、セットアップ、および初期化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c69cd-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="c69cd-113">Maquette の起動時:</span><span class="sxs-lookup"><span data-stu-id="c69cd-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="c69cd-114">プロジェクトが読み込まれるたびに、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c69cd-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="c69cd-115">プロジェクトは、それぞれのプロジェクトスクリプトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="c69cd-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="c69cd-116">JavaScript の実装</span><span class="sxs-lookup"><span data-stu-id="c69cd-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="c69cd-117">Maquette で使用される JavaScript インタープリターは、 [Jint](https://github.com/sebastienros/jint)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c69cd-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="c69cd-118">Jint は ECMAScript 5.1 と互換性があり、 [ecmascript 6 からの追加の拡張機能](https://github.com/sebastienros/jint/issues/343)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c69cd-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="c69cd-119">この拡張機能 `.mqjs` は、Maquette javascript ファイルを通常の javascript と区別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c69cd-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="c69cd-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c69cd-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->