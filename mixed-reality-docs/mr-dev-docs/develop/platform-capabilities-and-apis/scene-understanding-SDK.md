---
title: シーンを理解する SDK
description: シーンについて理解する SDK のプログラミングガイド
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: シーンの理解、空間マッピング、Windows Mixed Reality、Unity
ms.openlocfilehash: 7541ab38cd8c90e774614af5ea457e5636ee66fe
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684951"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="23d06-104">シーンについて SDK の概要</span><span class="sxs-lookup"><span data-stu-id="23d06-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="23d06-105">シーンを理解することは、Mixed Reality デバイスによってキャプチャされた非構造化環境センサーデータを変換し、を直感的かつ簡単に開発できる強力で抽象化された表現に変換することです。</span><span class="sxs-lookup"><span data-stu-id="23d06-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="23d06-106">SDK は、アプリケーションとシーンのランタイムを理解するための通信レイヤーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="23d06-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="23d06-107">3d 表現の3D シーングラフや2D アプリケーション用の2D 四角形とパネルなど、既存の標準構成要素を模倣することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="23d06-107">It's aimed to mimic existing standard constructs such as 3D scene graphs for 3D representations and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="23d06-108">シーン認識の模倣は、使用する可能性のある具象フレームワークにマップされますが、一般に SceneUnderstanding はフレームワークに依存しないため、相互にやり取りする多様なフレームワーク間の相互運用が可能です。</span><span class="sxs-lookup"><span data-stu-id="23d06-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="23d06-109">シーンを理解することは、SDK の役割を進化させることで、新しい表現と機能が統合されたフレームワーク内で引き続き公開されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="23d06-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="23d06-110">このドキュメントでは、まず、開発環境や使用状況について理解を深め、特定のクラスと構成要素に関するより詳細なドキュメントを提供するための概要を紹介します。</span><span class="sxs-lookup"><span data-stu-id="23d06-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="23d06-111">SDK はどこで入手できますか?</span><span class="sxs-lookup"><span data-stu-id="23d06-111">Where do I get the SDK?</span></span>

<span data-ttu-id="23d06-112">SceneUnderstanding SDK は NuGet を使用してダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="23d06-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="23d06-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="23d06-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="23d06-114">**注:** 最新リリースはプレビューパッケージに依存しており、プレリリースパッケージを表示するには、そのパッケージを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="23d06-115">バージョン 0.5.2022-rc では、シーンの理解によって C# および C++ の言語予測がサポートされるため、アプリケーションは Win32 または UWP プラットフォーム用のアプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="23d06-116">このバージョンの場合、SceneUnderstanding では、HoloLens2 との通信専用に使用される SceneObserver を除いて、unity のエディター内でのサポートをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="23d06-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="23d06-117">SceneUnderstanding には Windows SDK バージョン18362以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="23d06-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="23d06-118">Unity プロジェクトで SDK を使用している場合は、 [unity 用の NuGet](https://github.com/GlitchEnzo/NuGetForUnity) を使用して、パッケージをプロジェクトにインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="23d06-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="23d06-119">概念</span><span class="sxs-lookup"><span data-stu-id="23d06-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="23d06-120">シーン</span><span class="sxs-lookup"><span data-stu-id="23d06-120">The Scene</span></span>

<span data-ttu-id="23d06-121">混合の現実のデバイスは、環境内で認識されている内容に関する情報を常に統合しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="23d06-122">シーンは、これらすべてのデータソースをじょうごし、1つのまとまりを持つ抽象化を生成します。</span><span class="sxs-lookup"><span data-stu-id="23d06-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="23d06-123">シーンを理解すると、1つの物のインスタンスを表す [SceneObjects](scene-understanding-SDK.md#sceneobjects) の構成であるシーンが生成されます。シーンオブジェクト自体は、この SceneObject を構成する粒度の細かい部分を表す [SceneComponents](scene-understanding-SDK.md#scenecomponents) の合成です。</span><span class="sxs-lookup"><span data-stu-id="23d06-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="23d06-124">コンポーネントの例としては、四角形やメッシュなどがありますが、将来的には、境界ボックス、衝突メッシュ、メタデータなどを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="23d06-125">生のセンサーデータをシーンに変換するプロセスは、非常に大きなスペース (~ 10x10m) が非常に大きい場合 (~ 50x50m)、アプリケーションの要求なしにデバイスによって計算されているものではない、コストがかかる可能性のある操作です。</span><span class="sxs-lookup"><span data-stu-id="23d06-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="23d06-126">代わりに、必要に応じて、アプリケーションによってシーン生成がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="23d06-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="23d06-127">SceneObserver クラスには、シーンを計算または逆シリアル化できる静的メソッドがあります。このメソッドを使用して、列挙および操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="23d06-128">"Compute" アクションは要求時に実行され、CPU ではなく、別のプロセス (Mixed Reality ドライバー) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="23d06-129">ただし、別のプロセスで計算を行う場合、結果として得られるシーンデータは、アプリケーションのシーンオブジェクトに格納され、保持されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="23d06-130">このプロセスフローを示す図を以下に示します。また、2つのアプリケーションの例を示します。</span><span class="sxs-lookup"><span data-stu-id="23d06-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![プロセス図](images/SU-ProcessFlow.png)

<span data-ttu-id="23d06-132">左側には、常にオンで、独自のプロセスで実行されている mixed reality ランタイムの図があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="23d06-133">このランタイムは、デバイスの追跡や空間マッピングなどの操作を実行します。また、シーンを理解することで、世界についての理解と理由を理解するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="23d06-134">図の右側には、シーンの理解を活用する2つの理論的なアプリケーションが示されています。</span><span class="sxs-lookup"><span data-stu-id="23d06-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="23d06-135">最初のアプリケーションは、シーンを理解する SDK を使用する MRTK とのインターフェイスを使用して、2つの異なるシーンインスタンスを計算して使用します。</span><span class="sxs-lookup"><span data-stu-id="23d06-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="23d06-136">この図の3つのすべてのシーンでは、個別のインスタンスが生成されます。ドライバーは、アプリケーション間で共有されるグローバル状態を追跡しません。また、1つのシーンのシーンオブジェクトが別のシーンで見つからないことを示します。</span><span class="sxs-lookup"><span data-stu-id="23d06-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="23d06-137">シーンを理解することは、時間の経過と共に追跡するメカニズムを提供しますが、これは SDK を使用して行われます。この追跡を実行するコードは、アプリのプロセスで SDK で実行されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="23d06-138">各シーンでは、アプリケーションのメモリ領域にデータが格納されるため、シーンオブジェクトまたはその内部データのすべての関数がアプリケーションのプロセスで常に実行されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="23d06-139">Layout</span><span class="sxs-lookup"><span data-stu-id="23d06-139">Layout</span></span>

<span data-ttu-id="23d06-140">シーンを理解するには、ランタイムが論理的および物理的にコンポーネントを表す方法を理解し、理解しておくことが重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="23d06-141">シーンは、主要な改訂を必要とせずに将来の要件を満たすように pliable された、基になる構造を維持しながら、単純なレイアウトを持つデータを表します。</span><span class="sxs-lookup"><span data-stu-id="23d06-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="23d06-142">このシーンでは、すべてのコンポーネント (すべてのシーンオブジェクトの構成要素) をフラットリストに格納し、特定のコンポーネントが他のコンポーネントを参照する参照を使用して階層とコンポジションを定義します。</span><span class="sxs-lookup"><span data-stu-id="23d06-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="23d06-143">次に、フラットフォームと論理形式の両方で構造体の例を示します。</span><span class="sxs-lookup"><span data-stu-id="23d06-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="23d06-144">論理レイアウト</span><span class="sxs-lookup"><span data-stu-id="23d06-144">Logical Layout</span></span></th><th><span data-ttu-id="23d06-145">物理レイアウト</span><span class="sxs-lookup"><span data-stu-id="23d06-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="23d06-146">Scene</span><span class="sxs-lookup"><span data-stu-id="23d06-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="23d06-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="23d06-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="23d06-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="23d06-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="23d06-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="23d06-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="23d06-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="23d06-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="23d06-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="23d06-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="23d06-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="23d06-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="23d06-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="23d06-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="23d06-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="23d06-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="23d06-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="23d06-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="23d06-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="23d06-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="23d06-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="23d06-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="23d06-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="23d06-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="23d06-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="23d06-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="23d06-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="23d06-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="23d06-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="23d06-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="23d06-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="23d06-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="23d06-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="23d06-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="23d06-164">この図は、シーンの物理的レイアウトと論理的レイアウトの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="23d06-165">左側には、シーンを列挙するときにアプリケーションに表示されるデータの階層型レイアウトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="23d06-166">右側には、必要に応じて個別にアクセスできる12個の個別のコンポーネントで構成されたシーンがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="23d06-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="23d06-167">新しいシーンを処理する場合、アプリケーションはこの階層を論理的にウォークすることを想定していますが、シーンの更新間を追跡する場合、一部のアプリケーションは、2つのシーン間で共有される特定のコンポーネントを対象にするだけでよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="23d06-168">API の概要</span><span class="sxs-lookup"><span data-stu-id="23d06-168">API overview</span></span>

<span data-ttu-id="23d06-169">次のセクションでは、シーンについて理解するための構造の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="23d06-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="23d06-170">このセクションを読むと、シーンの表現方法や、さまざまなコンポーネントがどのように使用されるかについて理解できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="23d06-171">次のセクションでは、具体的なコード例と、この概要でここしている追加の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="23d06-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="23d06-172">以下で説明するすべての型は、 `Microsoft.MixedReality.SceneUnderstanding` 名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="23d06-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="23d06-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="23d06-173">SceneComponents</span></span>

<span data-ttu-id="23d06-174">これで、背後の論理的なレイアウトを理解できるようになったので、SceneComponents の概念と、それらを使用して階層を構築する方法を提示できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="23d06-175">SceneComponents は、メッシュ、クワッド、境界ボックスなど、1つのコアを表す SceneUnderstanding の最も詳細な decompositions です。</span><span class="sxs-lookup"><span data-stu-id="23d06-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="23d06-176">SceneComponents は、独立して更新でき、他の SceneComponents が参照できるものです。したがって、この種の追跡/参照メカニズムを可能にする一意の Id を持つ単一のグローバルプロパティを持つことになります。</span><span class="sxs-lookup"><span data-stu-id="23d06-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="23d06-177">Id は、シーン階層の論理構成およびオブジェクトの永続化 (あるシーンを別のシーンに更新する操作) に使用されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="23d06-178">新しく計算されたすべてのシーンを個別として処理し、その中のすべてのデータを列挙するだけで、Id は主に透過的になります。</span><span class="sxs-lookup"><span data-stu-id="23d06-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="23d06-179">ただし、複数の更新プログラムでコンポーネントの追跡を計画している場合は、これらの Id を使用して、シーンオブジェクト間の SceneComponents のインデックス作成と検索を行います。</span><span class="sxs-lookup"><span data-stu-id="23d06-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="23d06-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="23d06-180">SceneObjects</span></span>

<span data-ttu-id="23d06-181">SceneObject は、"物" のインスタンスを表す SceneComponent です。たとえば、壁、床、天井、などです。Kind プロパティで表されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="23d06-182">SceneObjects は幾何学的であるため、空間内の場所を表す関数とプロパティがありますが、ジオメトリックや論理構造は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="23d06-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="23d06-183">代わりに、SceneObjects は、システムでサポートされているさまざまな表現を提供する他の SceneComponents、特に SceneQuads と SceneMeshes を参照します。</span><span class="sxs-lookup"><span data-stu-id="23d06-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="23d06-184">新しいシーンが計算されると、ほとんどの場合、アプリケーションは、目的の内容を処理するためにシーンの SceneObjects を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23d06-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="23d06-185">SceneObjects は、次のいずれかを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="23d06-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="23d06-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="23d06-187">説明</span><span class="sxs-lookup"><span data-stu-id="23d06-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="23d06-188">バックグラウンド</span><span class="sxs-lookup"><span data-stu-id="23d06-188">Background</span></span></td><td><span data-ttu-id="23d06-189">SceneObject は、他の認識された種類のシーンオブジェクトの1つでは <b>ない</b> ことがわかっています。</span><span class="sxs-lookup"><span data-stu-id="23d06-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="23d06-190">このクラスは不明と混同しないでください。背景が壁、床、天井などではないことがわかっています。不明なカテゴリはまだ分類されていません。</span><span class="sxs-lookup"><span data-stu-id="23d06-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="23d06-191">電話</span><span class="sxs-lookup"><span data-stu-id="23d06-191">Wall</span></span></td><td><span data-ttu-id="23d06-192">物理的な壁面。</span><span class="sxs-lookup"><span data-stu-id="23d06-192">A physical wall.</span></span> <span data-ttu-id="23d06-193">壁面は、移動可能な環境構造であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="23d06-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="23d06-194">床</span><span class="sxs-lookup"><span data-stu-id="23d06-194">Floor</span></span></td><td><span data-ttu-id="23d06-195">床は、どのような面でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="23d06-196">注: 階段はフロアではありません。</span><span class="sxs-lookup"><span data-stu-id="23d06-196">Note: stairs are not floors.</span></span> <span data-ttu-id="23d06-197">また、このフロアは、明らかになる可能性があるため、1つの床面を明確に示すものではないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="23d06-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="23d06-198">複数レベルの構造、傾斜などすべてが floor として分類される必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="23d06-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="23d06-199">Ceiling</span></span></td><td><span data-ttu-id="23d06-200">部屋の上面。</span><span class="sxs-lookup"><span data-stu-id="23d06-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="23d06-201">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="23d06-201">Platform</span></span></td><td><span data-ttu-id="23d06-202">ホログラムを配置できる大きな平らなサーフェイス。</span><span class="sxs-lookup"><span data-stu-id="23d06-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="23d06-203">これらは、テーブル、countertops、およびその他の大きな水平サーフェスを表す傾向があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="23d06-204">World</span><span class="sxs-lookup"><span data-stu-id="23d06-204">World</span></span></td><td><span data-ttu-id="23d06-205">ラベル付けに依存しないジオメトリックデータ用に予約されたラベル。</span><span class="sxs-lookup"><span data-stu-id="23d06-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="23d06-206">EnableWorldMesh update フラグを設定することによって生成されるメッシュは、"世界" として分類されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="23d06-207">Unknown</span><span class="sxs-lookup"><span data-stu-id="23d06-207">Unknown</span></span></td><td><span data-ttu-id="23d06-208">このシーンオブジェクトはまだ分類されていないため、種類が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="23d06-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="23d06-209">これは、背景と混同しないようにしてください。このオブジェクトは何でもかまいません。システムは、十分な量の十分な分類を持っているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="23d06-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="23d06-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="23d06-210">SceneMesh</span></span>

<span data-ttu-id="23d06-211">SceneMesh は、トライアングルリストを使用して任意のジオメトリックオブジェクトのジオメトリを近似する SceneComponent です。</span><span class="sxs-lookup"><span data-stu-id="23d06-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="23d06-212">SceneMeshes は、いくつかの異なるコンテキストで使用されます。 watertight セル構造のコンポーネント、またはシーンに関連付けられている非バインド空間マッピングメッシュを表す WorldMesh として表現できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="23d06-213">各メッシュで提供されるインデックスと頂点データは、すべての最新のレンダリング Api で三角形メッシュをレンダリングするために使用される [頂点およびインデックスバッファー](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) と同じ使い慣れたレイアウトを使用します。</span><span class="sxs-lookup"><span data-stu-id="23d06-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="23d06-214">シーンの理解では、メッシュは32ビットのインデックスを使用し、特定のレンダリングエンジンのチャンクに分割する必要がある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="23d06-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="23d06-215">ワインディング順序と座標系</span><span class="sxs-lookup"><span data-stu-id="23d06-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="23d06-216">シーンの理解によって生成されるすべてのメッシュは、時計回りのワインディング順序を使用して右手座標系でメッシュを返すことが想定されています。</span><span class="sxs-lookup"><span data-stu-id="23d06-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="23d06-217">注: 191105 より前の OS ビルドでは既知のバグが発生する可能性があります。これは、"世界" メッシュが、後で修正された反時計回りのワインディング順序で返されています。</span><span class="sxs-lookup"><span data-stu-id="23d06-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="23d06-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="23d06-218">SceneQuad</span></span>

<span data-ttu-id="23d06-219">SceneQuad は、3d ワールドを占める2d 表面を表す SceneComponent です。</span><span class="sxs-lookup"><span data-stu-id="23d06-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="23d06-220">SceneQuads は ARKit Arkit Eanchor または Arkit プレーンと同様に使用できますが、フラットなアプリや拡張された UX で使用される2d キャンバスとして、より高度な機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="23d06-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="23d06-221">2D 固有の Api は、配置とレイアウトを簡単に使用できるようにするための四角形、および (レンダリングを除く) 四角形での開発には3d メッシュよりも2d キャンバスの方が似ています。</span><span class="sxs-lookup"><span data-stu-id="23d06-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="23d06-222">SceneQuad 図形</span><span class="sxs-lookup"><span data-stu-id="23d06-222">SceneQuad shape</span></span>

<span data-ttu-id="23d06-223">SceneQuads は、境界のある四角形の表面を2d で定義します。</span><span class="sxs-lookup"><span data-stu-id="23d06-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="23d06-224">ただし、SceneQuads は、任意の複雑な可能性のある図形 (ドーナツの形のテーブルなど) を含むサーフェイスを表します。クワッドの表面の複雑な形状を表すために、GetSurfaceMask API を使用して、指定したイメージバッファーにサーフェイスの形状をレンダリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="23d06-225">クワッドを持つ SceneObject にメッシュがある場合、メッシュの三角形は、このレンダリングされたイメージと同じである必要があり、両方とも2d 座標または3d 座標で表面の実際のジオメトリを表します。</span><span class="sxs-lookup"><span data-stu-id="23d06-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="23d06-226">シーンについて SDK の詳細とリファレンス</span><span class="sxs-lookup"><span data-stu-id="23d06-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="23d06-227">次のセクションでは、SceneUnderstanding の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="23d06-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="23d06-228">このセクションでは、サンプルアプリケーションを参照して、SceneUnderstanding がどのように総合的に使用されているかを確認するのに十分なコンテキストがある点について説明します。</span><span class="sxs-lookup"><span data-stu-id="23d06-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="23d06-229">初期化</span><span class="sxs-lookup"><span data-stu-id="23d06-229">Initialization</span></span>

<span data-ttu-id="23d06-230">SceneUnderstanding を操作するための最初の手順は、アプリケーションが Scene オブジェクトへの参照を取得することです。</span><span class="sxs-lookup"><span data-stu-id="23d06-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="23d06-231">これは、2つの方法のいずれかで実行できます。シーンはドライバーによって計算されるか、過去に計算された既存のシーンを逆シリアル化することができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="23d06-232">後者は、開発時に SceneUnderstanding を使用する場合に特に便利です。この場合、アプリケーションとエクスペリエンスは、mixed reality デバイスなしで簡単にプロトタイプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="23d06-233">シーンは SceneObserver を使用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="23d06-234">シーンを作成する前に、アプリケーションがデバイスを照会して、SceneUnderstanding をサポートしていることを確認し、SceneUnderstanding が必要とする情報に対するユーザーアクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="23d06-235">RequestAccessAsync () が呼び出されていない場合、新しいシーンを計算することはできません。</span><span class="sxs-lookup"><span data-stu-id="23d06-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="23d06-236">次に、Mixed Reality ヘッドセットを中心とした新しいシーンを計算し、10個の測定半径を持ちます。</span><span class="sxs-lookup"><span data-stu-id="23d06-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="23d06-237">データからの初期化 (別名、</span><span class="sxs-lookup"><span data-stu-id="23d06-237">Initialization from Data (aka.</span></span> <span data-ttu-id="23d06-238">PC パス)</span><span class="sxs-lookup"><span data-stu-id="23d06-238">the PC Path)</span></span>

<span data-ttu-id="23d06-239">直接消費するためのシーンは計算できますが、後で使用できるようにシリアル化された形式で計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="23d06-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="23d06-240">これは、開発者がデバイスを使用しなくてもシーンの理解を深めることができるように、開発に非常に役立つことが実証されています。</span><span class="sxs-lookup"><span data-stu-id="23d06-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="23d06-241">シーンをシリアル化する操作は、それを計算することとほぼ同じです。データは、SDK によってローカルで逆シリアル化されるのではなく、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="23d06-242">その後、自分で逆シリアル化したり、将来使用するために保存したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="23d06-243">SceneObject 列挙型</span><span class="sxs-lookup"><span data-stu-id="23d06-243">SceneObject Enumeration</span></span>

<span data-ttu-id="23d06-244">アプリケーションにシーンが作成されたので、アプリケーションは SceneObjects と対話します。</span><span class="sxs-lookup"><span data-stu-id="23d06-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="23d06-245">これを行うには、 **SceneObjects** プロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="23d06-245">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="23d06-246">コンポーネントの更新とコンポーネントの再検出</span><span class="sxs-lookup"><span data-stu-id="23d06-246">Component update and re-finding components</span></span>

<span data-ttu-id="23d06-247">***Findcomponent*** というシーン内のコンポーネントを取得する関数もあります。</span><span class="sxs-lookup"><span data-stu-id="23d06-247">There is another function that retrieves components in the Scene called ***FindComponent*** .</span></span> <span data-ttu-id="23d06-248">この関数は、追跡オブジェクトを更新し、それを後続のシーンで検索する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="23d06-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="23d06-249">次のコードでは、前のシーンに対して相対的な新しいシーンを計算し、新しいシーンでフロアを検索します。</span><span class="sxs-lookup"><span data-stu-id="23d06-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="23d06-250">シーンオブジェクトからのメッシュと四角形へのアクセス</span><span class="sxs-lookup"><span data-stu-id="23d06-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="23d06-251">SceneObjects が見つかると、ほとんどの場合、アプリケーションは、構成されている四角形やメッシュに含まれるデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="23d06-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="23d06-252">このデータには、[ ***四角形*** と ***メッシュ*** ] プロパティを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="23d06-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="23d06-253">次のコードは、floor オブジェクトのすべての四角形とメッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="23d06-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="23d06-254">これは、シーンオリジンに対する変換を含む SceneObject であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="23d06-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="23d06-255">これは、SceneObject が "事柄" のインスタンスを表し、スペースで参照できるため、四角形とメッシュが親を基準として変換されるジオメトリを表しているためです。</span><span class="sxs-lookup"><span data-stu-id="23d06-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="23d06-256">個別の SceneObjects が同じ SceneMesh/SceneQuad SceneComponents を参照している可能性があります。また、SceneObject に複数の SceneMesh/SceneQuad がある可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="23d06-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="23d06-257">変換の処理</span><span class="sxs-lookup"><span data-stu-id="23d06-257">Dealing with Transforms</span></span>

<span data-ttu-id="23d06-258">シーンの理解により、変換を処理するときに、従来の3D シーン表現に合わせて意図的に配置しようとしました。</span><span class="sxs-lookup"><span data-stu-id="23d06-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="23d06-259">そのため、各シーンは、最も一般的な3D 環境表現と同じように、1つの座標系に限定されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="23d06-260">SceneObjects は、その座標系内の位置と方向として場所を提供します。</span><span class="sxs-lookup"><span data-stu-id="23d06-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="23d06-261">アプリケーションが、1つのオリジンが提供する機能の制限を拡大するシーンを処理している場合は、SceneObjects を SpatialAnchors に固定するか、複数のシーンを生成して結合することができますが、わかりやすくするために、watertight のシーンが独自のオリジンに存在することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="23d06-262">次の Unity コードは、Windows 認識と Unity Api を使用して、座標系をまとめて配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="23d06-263">Unity の世界の原点に対応する SpatialCoordinateSystem の取得の詳細[について](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced)は、「 [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) 」、および「」と「」と「」を参照してください `.ToUnity()` `System.Numerics.Matrix4x4` `UnityEngine.Matrix4x4` 。</span><span class="sxs-lookup"><span data-stu-id="23d06-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="23d06-264">各 `SceneObject` には、 `Position` プロパティとプロパティがあります。これを使用すると、を含むの原点を基準として、 `Orientation` 対応するコンテンツを配置でき `Scene` ます。</span><span class="sxs-lookup"><span data-stu-id="23d06-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="23d06-265">たとえば、次の例では、ゲームがシーンルートの子であることを前提として、そのローカル位置と回転を、指定されたに合わせて割り当て `SceneObject` ます。</span><span class="sxs-lookup"><span data-stu-id="23d06-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="23d06-266">Quad</span><span class="sxs-lookup"><span data-stu-id="23d06-266">Quad</span></span>

<span data-ttu-id="23d06-267">四角形は、2D の配置シナリオを容易にするように設計されており、2D キャンバス UX 要素の拡張機能と考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="23d06-268">四角形は SceneObjects のコンポーネントであり、3D でレンダリングできますが、クワッド Api 自体は、四角形が2D 構造体であると想定しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="23d06-269">エクステントや形などの情報を提供し、配置のための Api を提供します。</span><span class="sxs-lookup"><span data-stu-id="23d06-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="23d06-270">四角形は四角形のエクステントを持ちますが、任意の形の2D サーフェイスを表します。</span><span class="sxs-lookup"><span data-stu-id="23d06-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="23d06-271">3D 環境の四角形を操作するこれらの2D サーフェイス上の配置を有効にするには、この相互作用を可能にするユーティリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="23d06-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="23d06-272">現在、シーンの理解には、 **Findセンター** のほとんどの配置と **GetOcclusionMask** という2つの関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="23d06-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask** .</span></span> <span data-ttu-id="23d06-273">Findセンターのほとんどの配置は、オブジェクトを配置できるクワッド上の位置を特定し、指定した境界ボックスが基になるサーフェイスに存在することを保証するオブジェクトの最適な位置を検索する、高レベルの API です。</span><span class="sxs-lookup"><span data-stu-id="23d06-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="23d06-274">出力の座標は、他の windows の Rect 型と同じように、左上隅が (x = 0, y = 0) である "クワッド空間" のクワッドに対して相対的です。</span><span class="sxs-lookup"><span data-stu-id="23d06-274">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="23d06-275">独自のオブジェクトのオリジンを操作するときは、必ずこのことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="23d06-275">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="23d06-276">次の例では、中央の最も配置可能な場所を検索し、クワッドにホログラムを固定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23d06-276">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="23d06-277">手順1-4 は、特定のフレームワーク/実装に大きく依存しますが、テーマは類似している必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-277">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="23d06-278">クワッドは、空間でローカライズされた境界2D 平面を表すだけであることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-278">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="23d06-279">お使いのエンジンとフレームワークで、クワッドがどこにあるかを認識し、クワッドを基準としてオブジェクトをルート設定することにより、ホログラムは実際の世界に対して正しく配置されます。</span><span class="sxs-lookup"><span data-stu-id="23d06-279">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="23d06-280">メッシュ型</span><span class="sxs-lookup"><span data-stu-id="23d06-280">Mesh</span></span>

<span data-ttu-id="23d06-281">メッシュは、オブジェクトまたは環境の幾何学的表現を表します。</span><span class="sxs-lookup"><span data-stu-id="23d06-281">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="23d06-282">[空間マッピング](../../design/spatial-mapping.md)と同様に、各空間サーフェスメッシュで提供されるメッシュインデックスと頂点データは、すべての最新のレンダリング api で三角形メッシュをレンダリングするために使用される頂点およびインデックスバッファーと同じ使い慣れたレイアウトを使用します。</span><span class="sxs-lookup"><span data-stu-id="23d06-282">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="23d06-283">頂点位置は、の座標系で指定され `Scene` ます。</span><span class="sxs-lookup"><span data-stu-id="23d06-283">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="23d06-284">このデータを参照するために使用される特定の Api は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23d06-284">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="23d06-285">次のコードは、メッシュ構造から三角形リストを生成する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="23d06-285">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="23d06-286">インデックス/頂点バッファーは >= インデックスまたは頂点の数である必要がありますが、それ以外は任意にサイズを変更して、効率的なメモリの再利用を可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-286">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="23d06-287">シーン異なればを使用した開発</span><span class="sxs-lookup"><span data-stu-id="23d06-287">Developing with scene understandings</span></span>

<span data-ttu-id="23d06-288">この時点で、ランタイムと SDK について理解しているシーンのコア構成要素について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-288">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="23d06-289">電力と複雑さの大部分は、アクセスパターン、3D フレームワークとの対話、およびこれらの Api の上に記述できるツールによって、空間プランニング、ルーム分析、ナビゲーション、物理などのより高度なタスクを実行できます。これらをサンプルでキャプチャして、シナリオを適切な方向に導くことができるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="23d06-289">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="23d06-290">説明していないサンプルまたはシナリオがある場合は、お知らせください。必要なものをドキュメント化してプロトタイプを作成します。</span><span class="sxs-lookup"><span data-stu-id="23d06-290">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="23d06-291">サンプルコードはどこで入手できますか。</span><span class="sxs-lookup"><span data-stu-id="23d06-291">Where can I get sample code?</span></span>

<span data-ttu-id="23d06-292">Unity のサンプルコードについては、Unity の [サンプルページ](https://github.com/sceneunderstanding-microsoft/unitysample) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="23d06-292">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="23d06-293">このアプリケーションを使用すると、デバイスと通信してさまざまなシーンオブジェクトをレンダリングすることができます。または、シリアル化されたシーンを PC に読み込んで、デバイスを使用せずにシーンの理解を体験することができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-293">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="23d06-294">サンプルシーンはどこで入手できますか。</span><span class="sxs-lookup"><span data-stu-id="23d06-294">Where can I get sample scenes?</span></span>

<span data-ttu-id="23d06-295">HoloLens2 を持っている場合は、ComputeSerializedAsync の出力をファイルに保存し、独自の使いやすさで逆シリアル化することで、キャプチャしたすべてのシーンを保存できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-295">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="23d06-296">HoloLens2 デバイスを持っていないが、シーンを理解したい場合は、キャプチャ済みシーンをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d06-296">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="23d06-297">現在、シーンに関する理解のサンプルにはシリアル化されたシーンが付属しています。これをダウンロードして、独自の便利な方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="23d06-297">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="23d06-298">次の場所で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="23d06-298">You can find them here:</span></span>

[<span data-ttu-id="23d06-299">シーンについてのサンプルシーン</span><span class="sxs-lookup"><span data-stu-id="23d06-299">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="23d06-300">関連項目</span><span class="sxs-lookup"><span data-stu-id="23d06-300">See also</span></span>

* [<span data-ttu-id="23d06-301">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="23d06-301">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="23d06-302">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="23d06-302">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="23d06-303">Unity のサンプル</span><span class="sxs-lookup"><span data-stu-id="23d06-303">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
