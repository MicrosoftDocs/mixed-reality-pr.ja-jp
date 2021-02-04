---
title: Unity 用の MRTK の概要
description: クロスプラットフォームの Mixed Reality Toolkit で新しい Mixed Reality 開発者に提供されるすべてのものの概要を説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン 2, MRTK, ツール, SDK, HoloLens, HoloLens 2, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, クロスプラットフォーム
ms.openlocfilehash: 54ad49bbf4da577a398a0bfb12fbdc84cdff34d9
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238115"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="34707-104">Unity 用の MRTK の概要</span><span class="sxs-lookup"><span data-stu-id="34707-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="34707-106">Mixed Reality Toolkit (MRTK) とは</span><span class="sxs-lookup"><span data-stu-id="34707-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="34707-107">MRTK は、HoloLens が初めてリリースされてからずっとある、すばらしいオープンソースのツールキットです。</span><span class="sxs-lookup"><span data-stu-id="34707-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="34707-108">そのツールキットが今のような立ち位置にあるのは、勤勉な開発者コミュニティの貢献のおかげです。</span><span class="sxs-lookup"><span data-stu-id="34707-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="34707-109">過去 3 年間で、Microsoft では開発者コミュニティのフィードバックを受け、最も重要な懸念事項に対応するために MRTK v2 を構築しました。</span><span class="sxs-lookup"><span data-stu-id="34707-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="34707-110">Unity 用の MRTK は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="34707-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="34707-111">このツールキットをインストールする最も簡単な方法は、新しい Mixed Reality Feature Tool アプリケーションを使用することです。</span><span class="sxs-lookup"><span data-stu-id="34707-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="34707-112">[インストールと使用方法](welcome-to-mr-feature-tool.md)に関するページに従い、Mixed Reality Toolkit カテゴリの **Mixed Reality Toolkit Foundation** パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="34707-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span> 

<span data-ttu-id="34707-113">Unity 用 MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="34707-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="34707-114">MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォーム向けのアプリケーションの開発を高速化することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="34707-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="34707-115">このプロジェクトは、参入障壁を減らすこと、Mixed Reality アプリケーションを作成すること、全体の成長に応じてコミュニティに貢献することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="34707-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="34707-116">詳細については、[GitHub 上の MRTK のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34707-116">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="34707-117">MRTK v2 の新機能</span><span class="sxs-lookup"><span data-stu-id="34707-117">New with MRTK v2</span></span>

<span data-ttu-id="34707-118">これらのプラットフォーム ツールに込めた Microsoft の成果に注目して欲しいと考えています。</span><span class="sxs-lookup"><span data-stu-id="34707-118">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="34707-119">事実、Microsoft では MRTK バージョン 2 を使用して、アウトオブボックス設定エクスペリエンス (OOBE) などのすぐに使えるエクスペリエンスや Mixed Reality Tips アプリケーションを開発しました。</span><span class="sxs-lookup"><span data-stu-id="34707-119">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="34707-120">また、新しい HoloLens 2 機能は、まずは MRTK 経由で公開されることを期待していただいてかまいません。Microsoft では、お客様が当社のプラットフォーム上で開発を行ううえで、それが最適な方法であると確信しているからです。</span><span class="sxs-lookup"><span data-stu-id="34707-120">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="34707-121">モジュール式</span><span class="sxs-lookup"><span data-stu-id="34707-121">Modular</span></span>

<span data-ttu-id="34707-122">モジュール式の手法でビルドされているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34707-122">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="34707-123">実際に、これにはいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="34707-123">There are actually a few benefits to this.</span></span>  <span data-ttu-id="34707-124">プロジェクトを小規模に保ち、管理を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="34707-124">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="34707-125">さらに、スクリプト作成が可能なオブジェクトによってビルドされており、インターフェイス駆動型であるため、組み込みのコンポーネントをお客様独自のものに置き換えて、他のサービス、システム、およびプラットフォームをサポートすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="34707-125">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="34707-126">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="34707-126">Cross-platform</span></span>

<span data-ttu-id="34707-127">他のプラットフォームに関しては、クロスプラットフォームのサポートを備えています。</span><span class="sxs-lookup"><span data-stu-id="34707-127">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="34707-128">また、このことによって、すべての単一プラットフォームがサポートされるわけではありませんが、ビルド ターゲットを他のプラットフォームに切り替えたときに、どのツールキットのコードも中断されないことを保証しています。</span><span class="sxs-lookup"><span data-stu-id="34707-128">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="34707-129">モジュール式の設計による堅牢性と拡張性により、ARCore、ARKit、および OpenVR などの複数のプラットフォームをサポートするようにアプリが設定されます。</span><span class="sxs-lookup"><span data-stu-id="34707-129">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="34707-130">高いパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="34707-130">Performant</span></span>

<span data-ttu-id="34707-131">モバイル プラットフォームに対応し、パフォーマンスを考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="34707-131">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="34707-132">このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。</span><span class="sxs-lookup"><span data-stu-id="34707-132">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="34707-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="34707-133">See also</span></span>

* [<span data-ttu-id="34707-134">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="34707-134">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="34707-135">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="34707-135">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="34707-136">Unity 用 MRTK を使用した開発</span><span class="sxs-lookup"><span data-stu-id="34707-136">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="34707-137">MRTK - ドキュメント ホーム (GitHub)</span><span class="sxs-lookup"><span data-stu-id="34707-137">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="34707-138">HoloToolkit/MRTK から MRTK バージョン 2 への移植 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="34707-138">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
