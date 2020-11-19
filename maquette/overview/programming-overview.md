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
# <a name="programming-overview"></a><span data-ttu-id="f018a-104">プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="f018a-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![ロゴ](../images/MaquetteIcon.png) <span data-ttu-id="f018a-106">プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="f018a-106">Programming Overview</span></span>

<span data-ttu-id="f018a-107">Microsoft Maquette は、 [Jint](https://github.com/sebastienros/jint) インタープリターに基づく JavaScript (拡張機能付き ECMAScript 5.1) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f018a-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="f018a-108">この拡張機能 `.mqjs` は、Maquette javascript ファイルを通常の javascript と区別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f018a-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="f018a-109">Maquette オブジェクトとインターフェイスは、オブジェクトを介してアクセスおよびスクリプト化でき `Maquette` ます。</span><span class="sxs-lookup"><span data-stu-id="f018a-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="f018a-110">Maquette のオブジェクトとインターフェイスに関するドキュメントは、Maquette の API リファレンスで提供されています。</span><span class="sxs-lookup"><span data-stu-id="f018a-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="f018a-111">MaquetteScript は新たに追加され、流束になるため、変更が必要になります。</span><span class="sxs-lookup"><span data-stu-id="f018a-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="f018a-112">より詳細なドキュメントと更新プログラムがまもなく利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="f018a-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="f018a-113">スクリプトのスポットライト</span><span class="sxs-lookup"><span data-stu-id="f018a-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="f018a-114">サンプル/チュートリアルとして焦点を絞ったスクリプトのスポットライト</span><span class="sxs-lookup"><span data-stu-id="f018a-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="f018a-115">2倍のイメージ/キャプション–スポットライトページへのリンク</span><span class="sxs-lookup"><span data-stu-id="f018a-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="f018a-116">MaquetteScript の概要</span><span class="sxs-lookup"><span data-stu-id="f018a-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="f018a-117">Mqjs と JS</span><span class="sxs-lookup"><span data-stu-id="f018a-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="f018a-118">プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="f018a-118">Programming Model</span></span>
  * <span data-ttu-id="f018a-119">編集と実行</span><span class="sxs-lookup"><span data-stu-id="f018a-119">Editing vs. Running</span></span>
* <span data-ttu-id="f018a-120">プログラミングワークフローへのリンク</span><span class="sxs-lookup"><span data-stu-id="f018a-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="f018a-121">結果を共有するためのリンク</span><span class="sxs-lookup"><span data-stu-id="f018a-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="f018a-122">プログラミングワークフロー</span><span class="sxs-lookup"><span data-stu-id="f018a-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="f018a-123">TBD</span><span class="sxs-lookup"><span data-stu-id="f018a-123">TBD</span></span>
* <span data-ttu-id="f018a-124">REPL</span><span class="sxs-lookup"><span data-stu-id="f018a-124">REPL</span></span>
* <span data-ttu-id="f018a-125">スクリプト作成操作</span><span class="sxs-lookup"><span data-stu-id="f018a-125">Scripting operation</span></span>
* <span data-ttu-id="f018a-126">デバッガーの操作</span><span class="sxs-lookup"><span data-stu-id="f018a-126">Debugger operation</span></span>
* <span data-ttu-id="f018a-127">デバッグループ</span><span class="sxs-lookup"><span data-stu-id="f018a-127">Debugging loop</span></span>
* <span data-ttu-id="f018a-128">コードをコピー/貼り付けますか?</span><span class="sxs-lookup"><span data-stu-id="f018a-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="f018a-129">Mqjs スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="f018a-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="f018a-130">MaquetteScript ファイルを実行するには、Maquette のコンパニオンウィンドウに移動し、[スクリプト] タブを開いて、スクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="f018a-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="f018a-131">スクリプトを出荷していないため、一部のオプションはまだ機能しません。</span><span class="sxs-lookup"><span data-stu-id="f018a-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="f018a-132">VSCode エディターのワークフロー</span><span class="sxs-lookup"><span data-stu-id="f018a-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="f018a-133">VSCode 内から Maquette でスクリプトを評価するには、ユーザーは2つのコマンドを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="f018a-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="f018a-134">`CTRL-5` 選択されたテキストまたはカーソルがある行全体を評価します。</span><span class="sxs-lookup"><span data-stu-id="f018a-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="f018a-135">`CTRL-SHIFT-5` ファイル全体を評価します。</span><span class="sxs-lookup"><span data-stu-id="f018a-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="f018a-136">テキストは Maquette に送信され、JavaScript 環境で評価されます。結果は VSCode の出力コンソールに返されます。</span><span class="sxs-lookup"><span data-stu-id="f018a-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="f018a-137">これは REPL (read-eval-print-loop) として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f018a-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="f018a-138">最初の手順の例</span><span class="sxs-lookup"><span data-stu-id="f018a-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="f018a-139">VSCode で次のコードをファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f018a-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="f018a-140">コードまたはセクションだけを選択し、[実行] にヒットし `CTRL-5` ます。</span><span class="sxs-lookup"><span data-stu-id="f018a-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="f018a-141">これにより、キューブが作成され、前面に配置され、その色が変更されます。</span><span class="sxs-lookup"><span data-stu-id="f018a-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="f018a-142">拡張機能を使用して検索する例は他にもあります。</span><span class="sxs-lookup"><span data-stu-id="f018a-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="f018a-143">結果の共有</span><span class="sxs-lookup"><span data-stu-id="f018a-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="f018a-144">ユーザー/チーム間で共有する方法</span><span class="sxs-lookup"><span data-stu-id="f018a-144">How to share between users/teams</span></span>
* <span data-ttu-id="f018a-145">ドキュメントディレクトリの Zip プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f018a-145">Zip project in documents directory</span></span>
* <span data-ttu-id="f018a-146">プロジェクトをファイル共有にコピー</span><span class="sxs-lookup"><span data-stu-id="f018a-146">Copy project to file share</span></span>
* <span data-ttu-id="f018a-147">チーム共有のファイルの場所を Maquette チームに追加しています</span><span class="sxs-lookup"><span data-stu-id="f018a-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="f018a-148">TBD</span><span class="sxs-lookup"><span data-stu-id="f018a-148">TBD</span></span>
* <span data-ttu-id="f018a-149">インクルード、相対/絶対パスを使用した他の場所のコードの参照、モジュール</span><span class="sxs-lookup"><span data-stu-id="f018a-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="f018a-150">ライブラリ?</span><span class="sxs-lookup"><span data-stu-id="f018a-150">Libraries?</span></span>
* <span data-ttu-id="f018a-151">ランタイム サポート</span><span class="sxs-lookup"><span data-stu-id="f018a-151">Runtime support</span></span>
* <span data-ttu-id="f018a-152">未解決の外部処理-エントリが見つからないか、クラッシュしたときの動作</span><span class="sxs-lookup"><span data-stu-id="f018a-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="f018a-153">特定のオブジェクトに関連付けられているスクリプトを追加/編集/観察することはできますか。</span><span class="sxs-lookup"><span data-stu-id="f018a-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="f018a-154">このスクリプトを他の場所にコピーして貼り付けることはできますか。</span><span class="sxs-lookup"><span data-stu-id="f018a-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="f018a-155">オブジェクトのプロパティについて</span><span class="sxs-lookup"><span data-stu-id="f018a-155">What about object properties?</span></span>
  * <span data-ttu-id="f018a-156">シーン内のオブジェクトに名前を付ける</span><span class="sxs-lookup"><span data-stu-id="f018a-156">Naming objects in my scene?</span></span> <span data-ttu-id="f018a-157">(スクリプトの名前を変更します)</span><span class="sxs-lookup"><span data-stu-id="f018a-157">(renaming script with it)</span></span>
  * <span data-ttu-id="f018a-158">オブジェクトに関連付けられているスクリプトの THIS または SELF キーワード</span><span class="sxs-lookup"><span data-stu-id="f018a-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="f018a-159">オブジェクトを右クリックすると、関連付けられているコード (およびそのすべての階層) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f018a-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="f018a-160">UI で選択し、VSCode のコードで起動できますか。</span><span class="sxs-lookup"><span data-stu-id="f018a-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="f018a-161">スクリプトソースファイル内のオブジェクトに関連付けられているコードを保持しますか?</span><span class="sxs-lookup"><span data-stu-id="f018a-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="f018a-162">クリックしたときに、プロパティウィンドウをオブジェクトの上に移動しますか?</span><span class="sxs-lookup"><span data-stu-id="f018a-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="f018a-163">VR および [メイン] タブでは、</span><span class="sxs-lookup"><span data-stu-id="f018a-163">In VR and in main tab?</span></span>
* <span data-ttu-id="f018a-164">セキュリティの問題</span><span class="sxs-lookup"><span data-stu-id="f018a-164">Security Issues</span></span>
* <span data-ttu-id="f018a-165">テスト–未定の可能性がありますが、スクリプトでビデオまたはフレームの取得を提案できます</span><span class="sxs-lookup"><span data-stu-id="f018a-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="f018a-166">バグ報告メカニズムを持っている場合は、他のユーザーのためにスクリプトを使用してアクセスできるようにすることができます (?)...あとで</span><span class="sxs-lookup"><span data-stu-id="f018a-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="f018a-167">展開–結果を "共有" する方法、実行可能ファイルとしてパッケージ</span><span class="sxs-lookup"><span data-stu-id="f018a-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="f018a-168">デモの実行/制御 spectating/監視</span><span class="sxs-lookup"><span data-stu-id="f018a-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="f018a-169">プレーヤーモード</span><span class="sxs-lookup"><span data-stu-id="f018a-169">Player mode</span></span>
* <span data-ttu-id="f018a-170">共有用に "コンポーネント" を作成する方法についてのセグメントがあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="f018a-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="f018a-171">(未定)</span><span class="sxs-lookup"><span data-stu-id="f018a-171">(might  be tbd)</span></span>
  * <span data-ttu-id="f018a-172">#Include がありますか?</span><span class="sxs-lookup"><span data-stu-id="f018a-172">Is there #include?</span></span> <span data-ttu-id="f018a-173">これは純粋な JS を処理しますが、名前空間の競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f018a-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="f018a-174">Maquette が、名前付きオブジェクトを使用して他の maquette を組み込み、JS コードに一致させることはできますか。</span><span class="sxs-lookup"><span data-stu-id="f018a-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
