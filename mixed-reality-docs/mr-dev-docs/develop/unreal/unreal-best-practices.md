---
title: 全般的なベスト プラクティス
description: Unreal Engine で Mixed Reality アプリケーションを開発するための推奨されるすべてのベスト プラクティスの最新情報を提供します。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, エディター拡張機能, Unreal エディター, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584904"
---
# <a name="general-best-practices"></a><span data-ttu-id="82a9d-104">全般的なベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="82a9d-104">General best practices</span></span>

<span data-ttu-id="82a9d-105">Mixed Reality 用の Unreal Engine プロジェクトを作成するときに、すべての開発者に従うことをお勧めする一般的なベスト プラクティスを示します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-105">The following are some general best practices we recommend all developers follow when creating an Unreal Engine project for Mixed Reality.</span></span>

## <a name="constructors"></a><span data-ttu-id="82a9d-106">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="82a9d-106">Constructors</span></span>

<span data-ttu-id="82a9d-107">ブループリントで "コンストラクター" に相当するものが必要な場合は、Unreals の[コンストラクション スクリプト](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)を使用します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-107">If you need the equivalent of a "constructor" in blueprints, use Unreals' [construction script](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html).</span></span> <span data-ttu-id="82a9d-108">"BeginPlay" イベントを使用する場合と比較したときの最大の利点は、コンストラクター スクリプトは "エディター" でも実行されることです。</span><span class="sxs-lookup"><span data-stu-id="82a9d-108">The primary advantage over using "BeginPlay" events is the constructor script runs in the "editor" as well.</span></span> <span data-ttu-id="82a9d-109">ほとんどの場合、起動時に、またはコンパイル時でさえ、値をキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="82a9d-109">Most of the time the values can be cached right at the start or even at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="82a9d-110">コンストラクション スクリプトのサポート情報の詳細については、[エディター拡張機能の概要](unreal-editor-extensions.md#construction-scripts)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="82a9d-110">You can find more supporting information for Construction scripts in our [editor extensions overview](unreal-editor-extensions.md#construction-scripts).</span></span>

## <a name="3d-buttons-and-textures"></a><span data-ttu-id="82a9d-111">3D ボタンとテクスチャ</span><span class="sxs-lookup"><span data-stu-id="82a9d-111">3D buttons and textures</span></span>

<span data-ttu-id="82a9d-112">Mixed Reality アプリケーションで 3D ボタを作成したり、その使用を計画したりするときは、パフォーマンスについて考えるのが自然です。</span><span class="sxs-lookup"><span data-stu-id="82a9d-112">It's natural to think about performance when creating or planning to use 3D buttons in mixed reality applications.</span></span> <span data-ttu-id="82a9d-113">ただし、すべてのものをメッシュから 3D として認識されるようにする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="82a9d-113">However, not everything has to be made from meshes to be perceived as 3D.</span></span> <span data-ttu-id="82a9d-114">テクスチャが慎重に作成されている Paper2D を使用して 3D の外観を取得するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="82a9d-114">You have the option of using Paper2D with carefully crafted textures to get that 3D look.</span></span> <span data-ttu-id="82a9d-115">これは 3D "のように見える" ボタンの場合は非常にうまく機能しますが、クワッド上の加工された画像に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="82a9d-115">This works really well for buttons that "seem" 3D, but are just photoshopped images on a quad.</span></span> <span data-ttu-id="82a9d-116">これらの装飾的なバージョンは、[スプライト](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="82a9d-116">A fancy version of these is called a [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).</span></span>

## <a name="variants"></a><span data-ttu-id="82a9d-117">バリアント</span><span class="sxs-lookup"><span data-stu-id="82a9d-117">Variants</span></span>

<span data-ttu-id="82a9d-118">実行時に複数のオブジェクト構成を使用してシーンを作成するシナリオでは、[Unreal バリアント](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)を使用します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-118">Use [Unreal Variants](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) in scenarios where you're creating a scene with multiple object configurations at runtime.</span></span> <span data-ttu-id="82a9d-119">バリエーションには、変化する素材やメッシュを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="82a9d-119">Variations can include changing materials or meshes.</span></span> 

## <a name="animation"></a><span data-ttu-id="82a9d-120">アニメーション</span><span class="sxs-lookup"><span data-stu-id="82a9d-120">Animation</span></span>

<span data-ttu-id="82a9d-121">多数の "対話型アニメーション" を作成する場合は、[Spline コンポーネント](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (Spline "Mesh" コンポーネントではなく) と [Timeline ノード](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)を利用します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-121">Take advantage of the [Spline component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (not the Spline "Mesh" Component) and [Timeline nodes](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) if you're creating lots of "interactable animations".</span></span> 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a><span data-ttu-id="82a9d-122">通信</span><span class="sxs-lookup"><span data-stu-id="82a9d-122">Communications</span></span>

<span data-ttu-id="82a9d-123">オブジェクトを動的に見つけることが困難な場合や、複数のアクターとブループリントの間の通信に使用される帯域幅が多すぎる場合は、[Level ブループリント](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)を使用します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-123">Use a [Level Blueprint](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) if you're having trouble dynamically finding objects or using too much bandwidth to communicate between multiple actors and blueprints.</span></span> <span data-ttu-id="82a9d-124">Unreal Engine 4 は Unity とは異なり、すべてのものをコンポーネント内に置く必要がないことを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="82a9d-124">Remember, Unreal Engine 4 isn't like Unity, not everything has to be inside a component.</span></span> <span data-ttu-id="82a9d-125">Level ブループリントは、複数のアクター間の通信を単純化するための、完全に有効で推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="82a9d-125">Level Blueprints are a perfectly valid and recommended way of simplifying the communication between multiple actors.</span></span> <span data-ttu-id="82a9d-126">オブジェクト参照さえ、Level ブループリントの OnBeginPlay で起動時に "キャッシュ" することができます。</span><span class="sxs-lookup"><span data-stu-id="82a9d-126">Object references can even be "cached" at startup in the Level Blueprint's OnBeginPlay.</span></span>

## <a name="global-state"></a><span data-ttu-id="82a9d-127">グローバル状態</span><span class="sxs-lookup"><span data-stu-id="82a9d-127">Global state</span></span>

<span data-ttu-id="82a9d-128">多くの場合、スコア、レベル データ、プレーヤー固有の情報、または特定のオブジェクトにまったく属していない他のものなど、レベル固有の状態を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82a9d-128">You'll often need to store level-specific state like score, level data, player-specific information, or anything else that doesn't quite belong to a particular object.</span></span> <span data-ttu-id="82a9d-129">[GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html) を見落とさないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="82a9d-129">Don't overlook the [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html).</span></span> <span data-ttu-id="82a9d-130">ほとんどの人はその存在を忘れていますが、GameMode はレベルごとに作成でき、各レベルに固有のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="82a9d-130">Most people forget that it exists, but the GameMode can be created per level, and contain data specific to each level.</span></span>

## <a name="optimizing-blueprints"></a><span data-ttu-id="82a9d-131">ブループリントの最適化</span><span class="sxs-lookup"><span data-stu-id="82a9d-131">Optimizing Blueprints</span></span>

<span data-ttu-id="82a9d-132">ブループリントの検索に時間がかかりすぎる場合は、C++ のコードを書き直す前に、Unreal でブループリントを "ネイティブ化" します。</span><span class="sxs-lookup"><span data-stu-id="82a9d-132">If you're finding your blueprints to be too slow, let Unreal "nativize" your blueprints before resorting to rewriting the code in c++.</span></span> <span data-ttu-id="82a9d-133">独自のカスタム ソリューションを作成する前に、自動的な[ネイティブ化](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)を使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="82a9d-133">Try using the automatic [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) before creating your own custom solution.</span></span>

![包含のブループリント ネイティブ化方法が強調表示されているブループリントの設定](images/unreal-general-practices-img-01.jpg)
