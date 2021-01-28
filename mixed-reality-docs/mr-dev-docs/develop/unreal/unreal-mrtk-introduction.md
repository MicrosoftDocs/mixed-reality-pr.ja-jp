---
title: Unreal 用の MRTK の概要
description: Unreal 用の Mixed Reality Toolkit で新しい Mixed Reality 開発者に提供されるすべてのものの概要を説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン 2, MRTK, ツール, SDK, HoloLens, HoloLens 2, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, クロスプラットフォーム
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584831"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="b5148-104">Unreal 用の MRTK の概要</span><span class="sxs-lookup"><span data-stu-id="b5148-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="b5148-106">Mixed Reality Toolkit (MRTK) とは</span><span class="sxs-lookup"><span data-stu-id="b5148-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="b5148-107">MRTK は、HoloLens が初めてリリースされてからずっとある、すばらしいオープンソースのツールキットです。</span><span class="sxs-lookup"><span data-stu-id="b5148-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="b5148-108">そのツールキットが今のような立ち位置にあるのは、勤勉な開発者コミュニティの貢献のおかげです。</span><span class="sxs-lookup"><span data-stu-id="b5148-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="b5148-109">Unreal 用 Mixed Reality Toolkit (MRTK-Unreal) は、Unreal Engine を使用した Mixed Reality アプリケーションの開発に役立つように設計されたプラグイン、サンプル、ドキュメントの形式で構成される一連のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="b5148-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="b5148-110">現在、ツールキットは次のもので構成されています。</span><span class="sxs-lookup"><span data-stu-id="b5148-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="b5148-111">[Unreal 用 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)。Hololens 2 アプリケーション用の UX 機能を実装するためのコード、ブループリント、例が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b5148-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="b5148-112">[Unreal 用 Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)。パフォーマンス バジェットに収めながら、Mixed Reality アプリケーションの視覚的な忠実性を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="b5148-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="b5148-113">[GitHub にある MRTK のドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)を参照し、[UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) または [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) のインストール ガイドに従って作業を開始してください。</span><span class="sxs-lookup"><span data-stu-id="b5148-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="b5148-114">モジュール式</span><span class="sxs-lookup"><span data-stu-id="b5148-114">Modular</span></span>

<span data-ttu-id="b5148-115">MRTK Unreal はモジュール方式で構築されているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5148-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="b5148-116">必要なプラグインを見つけて選択し、必要に応じて追加または削除することができます。</span><span class="sxs-lookup"><span data-stu-id="b5148-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="b5148-117">この方法により、プロジェクトを小規模に保ち、管理を容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5148-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="b5148-118">高いパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b5148-118">Performant</span></span>

<span data-ttu-id="b5148-119">モバイル プラットフォームで動作するので、MRTK Unreal はパフォーマンスを考慮して構築されています。</span><span class="sxs-lookup"><span data-stu-id="b5148-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="b5148-120">このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。</span><span class="sxs-lookup"><span data-stu-id="b5148-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5148-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5148-121">See also</span></span>

* [<span data-ttu-id="b5148-122">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="b5148-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="b5148-123">Unreal 用 MRTK を使用した開発</span><span class="sxs-lookup"><span data-stu-id="b5148-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="b5148-124">UX Tools - インストール ガイド (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b5148-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="b5148-125">UX Tools - ドキュメント ホーム (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b5148-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="b5148-126">Graphics Tools - インストール ガイド (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b5148-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="b5148-127">Graphics Tools - ドキュメント ホーム (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b5148-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)