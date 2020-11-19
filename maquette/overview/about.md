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
# <a name="about-maquette"></a><span data-ttu-id="fca47-104">Maquette について</span><span class="sxs-lookup"><span data-stu-id="fca47-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="fca47-105">![ロゴ ](../images/MaquetteIcon.png) MaquetteScript の概要</span><span class="sxs-lookup"><span data-stu-id="fca47-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="fca47-106">Maquette は、標準 ECMA 5.1 Javascript を統合することにより、Maquette シーンとオブジェクトでの対話機能の投資を可能にします。これは VSCode 内から編集および実行できます。</span><span class="sxs-lookup"><span data-stu-id="fca47-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="fca47-107">オブジェクトのプロパティは、スクリプト内からの読み取りと設定、と呼ばれるオブジェクトメソッド、およびオブジェクトとシステムイベントに対して公開されます。</span><span class="sxs-lookup"><span data-stu-id="fca47-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="fca47-108">スクリプトは、スクリプトを介してアクセスできるシステムオブジェクトを使用して、Maquette 自体と対話することもできます。</span><span class="sxs-lookup"><span data-stu-id="fca47-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="fca47-109">ユーザーが対話できるさまざまな UI コントロールは、システムの一部です。</span><span class="sxs-lookup"><span data-stu-id="fca47-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="fca47-110">これらは、Maquette での作成時に追加することも、スクリプト内から作成および管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="fca47-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="fca47-111">これらの要素を使用したユーザー操作イベント (データ入力、クリックなど) は、イベントとしてスクリプトにも公開されます。</span><span class="sxs-lookup"><span data-stu-id="fca47-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="fca47-112">これらの追加機能を使用すると、実験からデータ可視化まで、混合現実ユーザーシナリオを探索、AR または VR で完全に実現されたエクスペリエンスまで、単純な複雑なシーンを構築できます。</span><span class="sxs-lookup"><span data-stu-id="fca47-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="fca47-113">60の同一ビデオ</span><span class="sxs-lookup"><span data-stu-id="fca47-113">60 second'ish video</span></span>
* <span data-ttu-id="fca47-114">エントリのタイトルカード</span><span class="sxs-lookup"><span data-stu-id="fca47-114">Entry Title Card</span></span>
  * <span data-ttu-id="fca47-115">Maquette での対話型混合現実コンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="fca47-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="fca47-116">スクリプト/対話機能/UI システム</span><span class="sxs-lookup"><span data-stu-id="fca47-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="fca47-117">チームまたはビデオのキャプションによる VO の歓迎</span><span class="sxs-lookup"><span data-stu-id="fca47-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="fca47-118">説明</span><span class="sxs-lookup"><span data-stu-id="fca47-118">explaining:</span></span>
  * <span data-ttu-id="fca47-119">interactive MR コンテンツの作成を可能にするためのスクリプトの基礎</span><span class="sxs-lookup"><span data-stu-id="fca47-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="fca47-120">非常に広範なブラシストロークでの使用方法について触れます</span><span class="sxs-lookup"><span data-stu-id="fca47-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="fca47-121">スクリプト vingette の動作</span><span class="sxs-lookup"><span data-stu-id="fca47-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="fca47-122">[作成中] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="fca47-122">Composing dialog box</span></span>
  * <span data-ttu-id="fca47-123">アウトラインからのアプリの作成 (料理アプリのデモ)</span><span class="sxs-lookup"><span data-stu-id="fca47-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="fca47-124">Photogrammetry モデルでの構成</span><span class="sxs-lookup"><span data-stu-id="fca47-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="fca47-125">トラブルシューティングガイドとの対話</span><span class="sxs-lookup"><span data-stu-id="fca47-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="fca47-126">VSCode でのデバッグスクリプトの画面ビュー</span><span class="sxs-lookup"><span data-stu-id="fca47-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="fca47-127">シーン内のオブジェクトからスクリプトへのアクセスを取得する</span><span class="sxs-lookup"><span data-stu-id="fca47-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="fca47-128">その他...</span><span class="sxs-lookup"><span data-stu-id="fca47-128">Etc...</span></span>
* <span data-ttu-id="fca47-129">終了時のタイトルのタイトルカード</span><span class="sxs-lookup"><span data-stu-id="fca47-129">Summary Title card at end</span></span>
  * <span data-ttu-id="fca47-130">Maquette へのリンク</span><span class="sxs-lookup"><span data-stu-id="fca47-130">Link to Maquette</span></span>
  * <span data-ttu-id="fca47-131">スクリプトの使用を開始するには</span><span class="sxs-lookup"><span data-stu-id="fca47-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="fca47-132">お知らせ/ステータス/コミュニティ</span><span class="sxs-lookup"><span data-stu-id="fca47-132">Announcements/status/community</span></span>
  * <span data-ttu-id="fca47-133">実行できる内容 (?) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fca47-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="fca47-134">フィードバックと、お役に立ち上げる方法</span><span class="sxs-lookup"><span data-stu-id="fca47-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="fca47-135">はじめに</span><span class="sxs-lookup"><span data-stu-id="fca47-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="fca47-136">例とサンプルアプリ</span><span class="sxs-lookup"><span data-stu-id="fca47-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="fca47-137">サポート</span><span class="sxs-lookup"><span data-stu-id="fca47-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="fca47-138">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="fca47-138">Send us feedback</span></span>

<span data-ttu-id="fca47-139">お客様のエクスペリエンスと結果についてご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="fca47-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="fca47-140">フィードバック、提案、バグレポートは常に歓迎します。</span><span class="sxs-lookup"><span data-stu-id="fca47-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="fca47-141">リンクを <></span><span class="sxs-lookup"><span data-stu-id="fca47-141"><Link?></span></span>