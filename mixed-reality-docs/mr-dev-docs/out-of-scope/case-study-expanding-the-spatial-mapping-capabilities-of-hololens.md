---
title: ケーススタディ-HoloLens の空間マッピング機能の拡張
description: Microsoft HoloLens 用の最初のアプリを作成する際には、デバイスでの空間マッピングの境界をどれだけまでにプッシュできるかについても説明しました。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間マッピング
ms.openlocfilehash: b6546c5c14c5a16f5218721d007bc83798bacfad
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687479"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="4b35f-104">ケーススタディ-HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="4b35f-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="4b35f-105">Microsoft HoloLens 用の最初のアプリを作成する際には、デバイスでの空間マッピングの境界をどれだけまでにプッシュできるかについても説明しました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="4b35f-106">Microsoft スタジオのソフトウェアエンジニアである Jeff Evertt は、新しいテクノロジがどのように開発され、ユーザーの実際の環境でのホログラムの配置方法をより細かく制御する必要がないかについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="4b35f-107">HoloLens 2 では、開発者向けの新しい [シーンランタイム](../design/scene-understanding.md)が実装されています。これは、環境を認識するアプリケーションの開発を直感的に行うように設計された、構造化された高レベルの環境表現を使用して、混合の現実開発</span><span class="sxs-lookup"><span data-stu-id="4b35f-107">HoloLens 2 implements a new [Scene Understanding Runtime](../design/scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="4b35f-108">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="4b35f-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="4b35f-109">空間マッピング以外</span><span class="sxs-lookup"><span data-stu-id="4b35f-109">Beyond spatial mapping</span></span>

<span data-ttu-id="4b35f-110">私たち[は、1](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)つの HoloLens での最初の試合の2つであるの[に対して](https://www.microsoft.com/p/fragments/9nblggh5ggm8)、私たちは私たちの試合に取り組んできましたが、ここでは、ユーザーの環境についてより高いレベルの理解が必要でした。</span><span class="sxs-lookup"><span data-stu-id="4b35f-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="4b35f-111">各ゲームには独自の配置ニーズがありました。たとえば、フラグメントでは、フロアやテーブルなどのさまざまなサーフェスを区別して、関連する場所に手掛かりを配置する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="4b35f-112">また、ソファや椅子など、holographic 文字が見られる可能性のある表面を特定できるようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="4b35f-113">Young Conker では、プレーヤーの部屋の中で、生成された画面をプラットフォームとして使用できるようにしたいと考えていました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="4b35f-114">これらのゲームの開発パートナーである[Asobo スタジオ](https://www.asobostudio.com/index.html)は、この問題に直面し、HoloLens の空間マッピング機能を拡張するテクノロジを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="4b35f-115">これを使用すると、プレーヤーの部屋を分析し、壁、テーブル、椅子、床などの表面を特定できます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="4b35f-116">また、holographic オブジェクトの最適な配置を決定するために、一連の制約に対して最適化する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="4b35f-117">空間を理解するコード</span><span class="sxs-lookup"><span data-stu-id="4b35f-117">The spatial understanding code</span></span>

<span data-ttu-id="4b35f-118">Asobo の元のコードを取って、このテクノロジをカプセル化するライブラリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="4b35f-119">Microsoft と Asobo は、このコードをオープンソースにし、独自のプロジェクトで使用できるように [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) で使用できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="4b35f-120">すべてのソースコードが含まれているので、ニーズに合わせてカスタマイズし、その機能強化をコミュニティと共有することができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="4b35f-121">C++ ソルバーのコードは、UWP DLL にラップされ、 [MixedRealityToolkit 内に含まれるドロップイン prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)を使用して Unity に公開されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="4b35f-122">Unity サンプルには多くの便利なクエリが含まれています。これを使用すると、壁上の空のスペースを検索したり、オブジェクトを天井に配置したり、床上の大きなスペースに配置したり、文字の位置を識別したり、その他のさまざまな空間を理解するクエリを実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="4b35f-123">HoloLens によって提供される空間マッピングソリューションは、問題のある領域全体のニーズに対応できるように設計されていますが、空間を認識するモジュールは、2つの特定のゲームのニーズをサポートするように構築されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="4b35f-124">そのため、そのソリューションは、特定のプロセスと一連の前提を中心に構築されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="4b35f-125">**固定サイズの playspace** : ユーザーは、init 呼び出しの最大 playspace サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-125">**Fixed size playspace** : The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="4b35f-126">**1 回限りのスキャンプロセス** : このプロセスには、ユーザーが再生領域を定義するための個別のスキャンフェーズが必要です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-126">**One-time scan process** : The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="4b35f-127">クエリ関数は、スキャンが完了するまで機能しません。</span><span class="sxs-lookup"><span data-stu-id="4b35f-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="4b35f-128">**ユーザー駆動型の playspace "描画"** : スキャンフェーズ中に、ユーザーが playspace を移動して表示し、含める必要がある領域を効果的に描画します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-128">**User driven playspace “painting”** : During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="4b35f-129">生成されたメッシュは、このフェーズでユーザーからのフィードバックを提供するために重要です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="4b35f-130">**屋内で home または office セットアップ** : クエリ関数は、フラットなサーフェイスと壁面を中心に設計されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-130">**Indoors home or office setup** : The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="4b35f-131">これは、ソフトな制限です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-131">This is a soft limitation.</span></span> <span data-ttu-id="4b35f-132">ただし、スキャンフェーズでは、主要軸と補助軸に沿ってメッシュテセレーションを最適化するために、主軸分析が完了します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="4b35f-133">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="4b35f-133">Room Scanning Process</span></span>

<span data-ttu-id="4b35f-134">空間を理解するためのモジュールを読み込むときは、最初にスペースをスキャンします。これにより、床、天井、壁など、使用可能なすべてのサーフェイスが識別され、ラベルが付けられます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="4b35f-135">スキャン処理中は、部屋を見て、スキャンに含める必要がある領域を "ペイント" します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="4b35f-136">このフェーズで見たメッシュは、どの部分がスキャンされているかをユーザーが知ることができる視覚的なフィードバックの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="4b35f-137">空間認識モジュールの DLL は、内部的に、8cm サイズの voxel キューブのグリッドとして playspace を格納します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="4b35f-138">スキャンの初期部分では、主要なコンポーネント分析が完了して、部屋の軸が決定されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="4b35f-139">内部的には、これらの軸に合わせて voxel 領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="4b35f-140">メッシュは、voxel ボリュームから isosurface を抽出することによって、約1秒ごとに生成されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![白の空間マッピングメッシュと、緑色の playspace メッシュについて理解する](images/spatial-mapping-500px.png)

<span data-ttu-id="4b35f-142">白の空間マッピングメッシュと、緑色の playspace メッシュについて理解する</span><span class="sxs-lookup"><span data-stu-id="4b35f-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="4b35f-143">含まれている SpatialUnderstanding.cs ファイルは、スキャンフェーズプロセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="4b35f-144">次の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-144">It calls the following functions:</span></span>
* <span data-ttu-id="4b35f-145">**SpatialUnderstanding_Init** : 開始時に1回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-145">**SpatialUnderstanding_Init** : Called once at the start.</span></span>
* <span data-ttu-id="4b35f-146">**GeneratePlayspace_InitScan** : スキャンフェーズを開始する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-146">**GeneratePlayspace_InitScan** : Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="4b35f-147">**GeneratePlayspace_UpdateScan_DynamicScan** : 各フレームを呼び出して、スキャンプロセスを更新します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-147">**GeneratePlayspace_UpdateScan_DynamicScan** : Called each frame to update the scanning process.</span></span> <span data-ttu-id="4b35f-148">カメラの位置と向きは、前に説明した playspace の描画プロセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="4b35f-149">**GeneratePlayspace_RequestFinish** : playspace を終了するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-149">**GeneratePlayspace_RequestFinish** : Called to finalize the playspace.</span></span> <span data-ttu-id="4b35f-150">これは、スキャンフェーズ中に "描画された" 領域を使用して、playspace を定義およびロックします。</span><span class="sxs-lookup"><span data-stu-id="4b35f-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="4b35f-151">アプリケーションでは、スキャンフェーズ中に統計のクエリを実行したり、ユーザーフィードバックを提供するためにカスタムメッシュを照会したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="4b35f-152">**Import_UnderstandingMesh** : スキャン中に、モジュールによって提供された **SpatialUnderstandingCustomMesh** の動作が、prefab を理解するために、プロセスによって生成されたカスタムメッシュを定期的に照会します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-152">**Import_UnderstandingMesh** : During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="4b35f-153">さらに、この処理は、スキャンが完了した後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="4b35f-154">**SpatialUnderstanding** 動作によって実行されるスキャンフローは、 **initscan** を呼び出し、その後、各フレームに対して **アップデートを実行** します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan** , then **UpdateScan** each frame.</span></span> <span data-ttu-id="4b35f-155">統計クエリによって適切なカバレッジが報告されると、ユーザーは、[ **Requestfinish** ] を呼び出して、スキャンフェーズの終了を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="4b35f-156">戻り値が DLL の処理を完了したことを示すまで、アップデートを引き続き呼び出す **ことができ** ます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="4b35f-157">クエリ</span><span class="sxs-lookup"><span data-stu-id="4b35f-157">The queries</span></span>

<span data-ttu-id="4b35f-158">スキャンが完了すると、インターフェイスで次の3種類のクエリにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="4b35f-159">**トポロジクエリ** : スキャンされたルームのトポロジに基づく高速クエリです。</span><span class="sxs-lookup"><span data-stu-id="4b35f-159">**Topology queries** : These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="4b35f-160">**Shape クエリ** : トポロジクエリの結果を使用して、定義したカスタム図形に適した水平方向のサーフェイスを検索します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-160">**Shape queries** : These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="4b35f-161">**オブジェクト配置クエリ** : オブジェクトの一連のルールと制約に基づいて最適な場所を検索する、より複雑なクエリです。</span><span class="sxs-lookup"><span data-stu-id="4b35f-161">**Object placement queries** : These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="4b35f-162">3つの主要なクエリに加えて、raycasting インターフェイスを使用して、タグ付きサーフェスの種類を取得し、カスタムの watertight ルームメッシュをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="4b35f-163">トポロジクエリ</span><span class="sxs-lookup"><span data-stu-id="4b35f-163">Topology queries</span></span>

<span data-ttu-id="4b35f-164">DLL 内では、トポロジマネージャーは環境のラベル付けを処理します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="4b35f-165">前述のように、データの大部分は、voxel ボリューム内に含まれる、1つのデータに格納されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="4b35f-166">さらに、 **playspace** 情報構造体は、再生領域に関する情報を格納するために使用されます。これには、ワールドアラインメント (下記の詳細情報)、floor、および天井高さが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="4b35f-167">ヒューリスティックは、floor、シーリング、および壁面を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="4b35f-168">たとえば、1 ~ 2 の範囲を超える水平方向サーフェイスは、床面と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="4b35f-169">このプロセスでは、スキャン処理中のカメラパスも使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="4b35f-170">トポロジマネージャーによって公開されるクエリのサブセットは、DLL を通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="4b35f-171">公開されているトポロジクエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4b35f-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="4b35f-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="4b35f-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="4b35f-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="4b35f-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="4b35f-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="4b35f-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="4b35f-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="4b35f-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="4b35f-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="4b35f-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="4b35f-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="4b35f-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="4b35f-178">各クエリには、クエリの種類に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="4b35f-179">次の例では、必要なボリュームの最小の高さ & 幅、床の上の最小配置高さ、およびボリュームの前面にある最小のクリアランスの量をユーザーが指定しています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="4b35f-180">すべての測定値は、メーターで計算されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="4b35f-181">これらの各クエリは、 **TopologyResult** 構造体の事前に割り当てられた配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="4b35f-182">**Locationcount** パラメーターは、渡された配列の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="4b35f-183">戻り値は、返された場所の数を報告します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="4b35f-184">この数は、渡された **Locationcount** パラメーターを超えてはなりません。</span><span class="sxs-lookup"><span data-stu-id="4b35f-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="4b35f-185">**TopologyResult** には、返されたボリュームの中央の位置、フェーシングの方向 (通常は)、および検出された領域の大きさが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="4b35f-186">Unity サンプルでは、これらの各クエリが仮想 UI パネルのボタンにリンクされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="4b35f-187">サンプルでは、これらの各クエリのパラメーターを妥当な値にハードコーディングしています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="4b35f-188">その他の例については、サンプルコードの *SpaceVisualizer.cs* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="4b35f-189">クエリのシェイプ</span><span class="sxs-lookup"><span data-stu-id="4b35f-189">Shape queries</span></span>

<span data-ttu-id="4b35f-190">DLL 内で、shape analyzer ( **ShapeAnalyzer_W** ) は、トポロジアナライザーを使用して、ユーザーが定義したカスタム図形と照合します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-190">Inside of the DLL, the shape analyzer ( **ShapeAnalyzer_W** ) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="4b35f-191">Unity サンプルには、定義済みの一連の図形があります。これは、[クエリ] メニューの [図形] タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="4b35f-192">図形の分析は、水平方向のサーフェイスでのみ動作することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="4b35f-193">たとえば、ソファは、平らな座席の表面とソファの上面によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="4b35f-194">Shape クエリでは、特定のサイズ、高さ、および縦横範囲の2つのサーフェスが検索され、2つのサーフェスがアラインされ、接続されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="4b35f-195">この Api の用語を使用して、ソファ座席とソファの背面の上部には形状コンポーネントがあり、アラインメント要件はシェイプコンポーネントの制約です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="4b35f-196">"Sittable" オブジェクトの Unity サンプル ( **ShapeDefinition.cs** ) で定義されているクエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-196">An example query defined in the Unity sample ( **ShapeDefinition.cs** ), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="4b35f-197">各図形クエリは、一連の図形コンポーネントによって定義されます。各図形コンポーネントには、一連のコンポーネント制約と、コンポーネント間の依存関係を示す一連の図形制約があります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="4b35f-198">この例では、1つのコンポーネント定義に3つの制約が含まれており、コンポーネント間に図形の制約はありません (コンポーネントが1つだけであるため)。</span><span class="sxs-lookup"><span data-stu-id="4b35f-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="4b35f-199">これに対し、ソファ図形には、2つの図形コンポーネントと4つのシェイプ制約があります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="4b35f-200">コンポーネントは、ユーザーのコンポーネントリスト内のインデックスによって識別されることに注意してください (この例では0と 1)。</span><span class="sxs-lookup"><span data-stu-id="4b35f-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="4b35f-201">カスタム図形の定義を簡単に作成するために、Unity モジュールにラッパー関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="4b35f-202">コンポーネントとシェイプの制約の完全な一覧については、 **ShapeComponentConstraint** と **ShapeConstraint** の構造内の **SpatialUnderstandingDll.cs** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![青い四角形は、椅子の図形クエリの結果を強調表示します。](images/chair-shape-query-500px.png)

<span data-ttu-id="4b35f-204">青い四角形は、椅子の図形クエリの結果を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="4b35f-205">オブジェクト配置のソルバー</span><span class="sxs-lookup"><span data-stu-id="4b35f-205">Object placement solver</span></span>

<span data-ttu-id="4b35f-206">オブジェクト配置クエリを使用すると、オブジェクトを配置する物理的な部屋の理想的な場所を識別できます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="4b35f-207">ソルバーは、オブジェクトのルールと制約を指定して、最適な場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="4b35f-208">また、オブジェクトクエリは、オブジェクトが **Solver_RemoveObject** または **Solver_RemoveAllObjects** 呼び出しで削除されるまで保持され、制約された複数オブジェクト配置が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="4b35f-209">オブジェクト配置クエリは、3つの部分で構成されます。パラメーターを使用した配置の種類、規則の一覧、および制約の一覧です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="4b35f-210">クエリを実行するには、次の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-210">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="4b35f-211">この関数は、オブジェクト名、配置定義、および規則と制約の一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="4b35f-212">C# ラッパーは、規則と制約の構築を簡単にする構築ヘルパー関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="4b35f-213">配置定義には、次のいずれかのクエリの種類が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-213">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="4b35f-214">各配置型には、型に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="4b35f-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="4b35f-215">**Objectplacementdefinition** 構造体には、これらの定義を作成するための静的ヘルパー関数のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="4b35f-216">たとえば、床にオブジェクトを配置する場所を見つけるには、次の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="4b35f-217">配置の種類に加えて、一連のルールと制約を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="4b35f-218">規則に違反することはありません。</span><span class="sxs-lookup"><span data-stu-id="4b35f-218">Rules cannot be violated.</span></span> <span data-ttu-id="4b35f-219">型とルールを満たす配置場所は、最適な配置場所を選択するために、一連の制約に対して最適化されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="4b35f-220">各ルールと制約は、指定された静的作成関数によって作成できます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="4b35f-221">ルールと制約の構築関数の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="4b35f-222">次に示すオブジェクト配置クエリでは、画面の端に半分のメーターキューブを配置し、その他の場所にある他のオブジェクトから、ルームの中央付近に移動するための場所を探しています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="4b35f-223">成功した場合、配置位置、次元、および向きを含む **Objectplacement Ementresult** 構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="4b35f-224">また、配置は、配置されたオブジェクトの DLL の内部リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="4b35f-225">後続の配置クエリでは、このオブジェクトが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="4b35f-226">Unity サンプルの **LevelSolver.cs** ファイルには、クエリの例が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![青いボックスには、"カメラの位置から離れています" ルールを使用して、3か所のフロアクエリの結果が表示されます。](images/away-from-camera-position-500px.png)

<span data-ttu-id="4b35f-228">青いボックスには、"カメラの位置から離れています" ルールを使用して、3か所のフロアクエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="4b35f-229">**ヒント:**</span><span class="sxs-lookup"><span data-stu-id="4b35f-229">**Tips:**</span></span>
* <span data-ttu-id="4b35f-230">レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置位置を解決する場合は、まず、必要以上に大きなオブジェクトを解決して、スペースが見つかる確率を最大化します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="4b35f-231">配置順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-231">Placement order is important.</span></span> <span data-ttu-id="4b35f-232">オブジェクトの配置が見つからない場合は、制限の少ない構成を試してください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="4b35f-233">一連のフォールバック構成を設定することは、多くの部屋構成で機能をサポートするために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="4b35f-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="4b35f-234">射線のキャスト</span><span class="sxs-lookup"><span data-stu-id="4b35f-234">Ray casting</span></span>

<span data-ttu-id="4b35f-235">3つの主要なクエリに加えて、射線のキャストインターフェイスを使用して、タグ付きサーフェス型を取得できます。また、ルームがスキャンされて完了した後に、カスタムの watertight playspace メッシュをコピーできます。フロア、天井、壁などの表面には、ラベルが内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="4b35f-236">**PlayRaycastResult Eraycast** 関数は、光線を受け取り、光線が既知のサーフェイスと競合している場合は、その表面に関する情報を **RaycastResult** の形式で返します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult** .</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="4b35f-237">内部的には、raycast は、playspace の計算された8cm キューブ voxel 表現に対して計算されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="4b35f-238">各 voxel には、処理されたトポロジデータ (とも呼ばれます) を持つ surface 要素のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="4b35f-239">交差する voxel セルに含まれているが比較され、トポロジ情報の検索に使用される最適な一致が得られます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="4b35f-240">このトポロジデータには、 **SurfaceTypes** 列挙型の形式で返されるラベルと、交差するサーフェイスの表面領域が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="4b35f-241">Unity のサンプルでは、カーソルは各フレームに射線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="4b35f-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="4b35f-242">最初に、Unity の colliders に対して2番目は、モジュールの世界表現を理解するためのものです。最後に、UI 要素に対してを実行します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="4b35f-243">このアプリケーションでは、UI は優先順位を取得し、結果を理解し、最後に Unity の colliders を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b35f-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="4b35f-244">**SurfaceType** は、カーソルの横にテキストとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 結果レポートを床と交差させることができます。](images/raycast-result-500px.jpg)

<span data-ttu-id="4b35f-246">Raycast 結果レポートを床と交差させることができます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="4b35f-247">コードを取得する</span><span class="sxs-lookup"><span data-stu-id="4b35f-247">Get the code</span></span>

<span data-ttu-id="4b35f-248">オープンソースコードは [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)で入手できます。</span><span class="sxs-lookup"><span data-stu-id="4b35f-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="4b35f-249">プロジェクトでコードを使用する場合は、 [HoloLens Developer フォーラム](https://forums.hololens.com/) でお知らせください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="4b35f-250">何をしているかをお待ちください。</span><span class="sxs-lookup"><span data-stu-id="4b35f-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="4b35f-251">著者について</span><span class="sxs-lookup"><span data-stu-id="4b35f-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="4b35f-252"><b>Jeff Evertt</b> は、育成から開発を体験できるようになったころから HoloLens で働いてきたソフトウェアエンジニアリングリードです。</span><span class="sxs-lookup"><span data-stu-id="4b35f-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="4b35f-253">HoloLens より前は、さまざまなプラットフォームやゲームで Xbox Kinect とゲーム業界で働いていました。</span><span class="sxs-lookup"><span data-stu-id="4b35f-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="4b35f-254">Jeff は、ロボットやグラフィックス、そしてビープ音が鳴り目立つ色ライトを使用したことに情熱を持っています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="4b35f-255">新しいものを学習し、ソフトウェア、ハードウェア、特に2つの重なり合う領域で作業しています。</span><span class="sxs-lookup"><span data-stu-id="4b35f-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="4b35f-256">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b35f-256">See also</span></span>
* [<span data-ttu-id="4b35f-257">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4b35f-257">Spatial mapping</span></span>](../design/spatial-mapping.md)
* [<span data-ttu-id="4b35f-258">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="4b35f-258">Scene understanding</span></span>](../design/scene-understanding.md)
* [<span data-ttu-id="4b35f-259">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="4b35f-259">Room scan visualization</span></span>](../design/room-scan-visualization.md)
* [<span data-ttu-id="4b35f-260">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="4b35f-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="4b35f-261">Asobo Studio: HoloLens 開発の最前線からの教訓</span><span class="sxs-lookup"><span data-stu-id="4b35f-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
