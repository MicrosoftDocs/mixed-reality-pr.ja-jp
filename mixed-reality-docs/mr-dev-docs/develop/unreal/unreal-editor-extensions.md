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
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="545fc-104">Unreal のエディター拡張機能</span><span class="sxs-lookup"><span data-stu-id="545fc-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="545fc-105">Unreal には、エンジンをニーズに合わせてカスタマイズできる広範な機能セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="545fc-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="545fc-106">簡単ですが限的的なものから、非常に強力ですが複雑なものまで、幅広い機能があります。</span><span class="sxs-lookup"><span data-stu-id="545fc-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="545fc-107">以下の手順は、複雑さが増す順になっています。</span><span class="sxs-lookup"><span data-stu-id="545fc-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="545fc-108">一般に、問題のより簡単な解決策を探し、そのオプションを使い果たしたら、より複雑なオプションに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="545fc-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="545fc-109">例として、ほとんどの場合、プラグインの代わりに基本的なコンストラクション スクリプトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="545fc-110">コンストラクション スクリプト</span><span class="sxs-lookup"><span data-stu-id="545fc-110">Construction scripts</span></span>

<span data-ttu-id="545fc-111">コンストラクション スクリプトを使用して、Blueprint インスタンスの作成時に実行される初期化アクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="545fc-112">ユーザー コンストラクション スクリプト</span><span class="sxs-lookup"><span data-stu-id="545fc-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="545fc-113">ブループリントの例</span><span class="sxs-lookup"><span data-stu-id="545fc-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="545fc-114">ビデオ チュートリアル</span><span class="sxs-lookup"><span data-stu-id="545fc-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="545fc-115">スクリプト アクション</span><span class="sxs-lookup"><span data-stu-id="545fc-115">Scripted actions</span></span>

<span data-ttu-id="545fc-116">スクリプト アクションは、Editor Utility Blueprint です。</span><span class="sxs-lookup"><span data-stu-id="545fc-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="545fc-117">Unreal エディターで次のようにしてそれを起動できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="545fc-118">コンテンツ ブラウザーで **[Assets]\(アセット\)** を右クリックします</span><span class="sxs-lookup"><span data-stu-id="545fc-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="545fc-119">または、レベル ビューポートまたワールド アウトライナーで **[Actors]\(アクター\)** を右クリックします</span><span class="sxs-lookup"><span data-stu-id="545fc-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="545fc-120">スクリプト アクションは、アセットまたはアクターのセットについてのコンテキストをブループリントのロジックで認識する必要がある場合に、特に適しています。</span><span class="sxs-lookup"><span data-stu-id="545fc-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="545fc-121">通常、スクリプト アクションにより、アクションの実行時に選択したアセットまたはアクターのリストが取得され、それらのオブジェクトが変更されたり、グラフで考慮されたりします。</span><span class="sxs-lookup"><span data-stu-id="545fc-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="545fc-122">スクリプト アクション</span><span class="sxs-lookup"><span data-stu-id="545fc-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="545fc-123">プロジェクトの開始時にスクリプト アクションを実行する</span><span class="sxs-lookup"><span data-stu-id="545fc-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="545fc-124">Editor Utility Widget</span><span class="sxs-lookup"><span data-stu-id="545fc-124">Editor utility widgets</span></span>

<span data-ttu-id="545fc-125">新しい UI 要素を追加して Unreal エディターのユーザー インターフェイス (UI) を変更したいときはいつでも、[Editor Utility Widget](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="545fc-126">Editor Utility Widget は、Unreal Motion Graphics (UMG) に基づいているため、他の UMG Widget Blueprint の場合と同じように、ブループリントでウィジェットを設定できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="545fc-127">これらのウィジェットはエディター UI 専用であり、カスタム エディターのタブを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="545fc-128">その後、既存のエディターのタブを選択するのと同様に、[Windows]\(ウィンドウ\) メニューからこれらのカスタム タブを選択できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="545fc-129">プラグイン</span><span class="sxs-lookup"><span data-stu-id="545fc-129">Plugins</span></span>

<span data-ttu-id="545fc-130">Unreal を使用すると、UE4 のツールとランタイムで使用する独自のカスタム [プラグイン](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html)を開発して管理できます。</span><span class="sxs-lookup"><span data-stu-id="545fc-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="545fc-131">いつでも Unreal エディターでプラグインを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="545fc-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="545fc-132">プラグインを使用して、実行時のゲームプレイ機能を追加したり、エンジンの組み込み機能を変更したり、新しいファイルの種類を作成したり、エディターの機能を拡張したりできます。</span><span class="sxs-lookup"><span data-stu-id="545fc-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

