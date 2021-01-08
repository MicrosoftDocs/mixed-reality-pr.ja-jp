---
title: 空間メッシュの視覚化
description: MRTK での空間メッシュの視覚化を使用した設計ガイドラインと物理的な環境の理解について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality、HoloLens、UI コントロール、相互作用、UI、ux、UX デザイン、空間 UI、空間相互作用、3D UI、3D UX、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 0f9cdc218c6fe54b8892c39a6a76f023e203d334
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009922"
---
# <a name="spatial-mesh"></a><span data-ttu-id="d4800-104">空間メッシュ</span><span class="sxs-lookup"><span data-stu-id="d4800-104">Spatial mesh</span></span>

![空間メッシュ](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="d4800-106">ユーザーは、空間メッシュの視覚化によって、デバイスがどのように物理的な環境を認識し、理解しているかを学習します。</span><span class="sxs-lookup"><span data-stu-id="d4800-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="d4800-107">適切な空間メッシュの視覚化によって、空間コンテキストを提供しながら、すばらしいと魔法のエクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d4800-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="d4800-108">設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="d4800-108">Design guideline</span></span>

<span data-ttu-id="d4800-109">ユーザーがコンテンツにフォーカスを設定して操作できるようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="d4800-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="d4800-110">バックグラウンドでの空間メッシュの継続的な視覚化は、邪魔になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d4800-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="d4800-111">最初の起動時に1回だけ環境を表示しないようにすることをお勧めします。または、領域を対象にして環境メッシュを表示することをユーザーに明確に示すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4800-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="d4800-112">この動作は、Mixed Reality ポータルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="d4800-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d4800-113">Unity 用の MRTK (Mixed Reality Toolkit) での空間メッシュの視覚化</span><span class="sxs-lookup"><span data-stu-id="d4800-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="d4800-114">MRTK には、空間メッシュの視覚化に関するいくつかの素材が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d4800-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="d4800-115">**MRTK_Wireframe、MRTK_Wireframe ます**。既定の静的な空間メッシュマテリアルは、アニメーションを使用せずにメッシュの輪郭を表示します。</span><span class="sxs-lookup"><span data-stu-id="d4800-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="d4800-116">この資料は、空間メッシュジオメトリ全体を示すため、デバッグのために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d4800-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="d4800-117">ただし、運用環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="d4800-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="d4800-118">**MRTK_SurfaceReconstruction**: この資料では、空間メッシュにアニメーション化されたパルス効果を提供します。</span><span class="sxs-lookup"><span data-stu-id="d4800-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="d4800-119">このマテリアルを使用して、特定の時点またはユーザーのエアタップ入力で環境を視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="d4800-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="d4800-120">例については、「 **PulseShaderExamples** シーン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4800-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="d4800-121">詳細については、「 [Mrtk-空間認識](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 」と「 [Mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4800-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="d4800-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4800-122">See also</span></span>

* [<span data-ttu-id="d4800-123">カーソル</span><span class="sxs-lookup"><span data-stu-id="d4800-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d4800-124">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="d4800-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d4800-125">ボタン</span><span class="sxs-lookup"><span data-stu-id="d4800-125">Button</span></span>](button.md)
* [<span data-ttu-id="d4800-126">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="d4800-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d4800-127">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="d4800-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d4800-128">操作</span><span class="sxs-lookup"><span data-stu-id="d4800-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d4800-129">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="d4800-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d4800-130">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="d4800-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d4800-131">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="d4800-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d4800-132">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="d4800-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d4800-133">キーボード</span><span class="sxs-lookup"><span data-stu-id="d4800-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d4800-134">ヒント</span><span class="sxs-lookup"><span data-stu-id="d4800-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d4800-135">スレート</span><span class="sxs-lookup"><span data-stu-id="d4800-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="d4800-136">スライダー</span><span class="sxs-lookup"><span data-stu-id="d4800-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="d4800-137">シェーダー</span><span class="sxs-lookup"><span data-stu-id="d4800-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="d4800-138">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="d4800-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d4800-139">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="d4800-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d4800-140">表面吸着</span><span class="sxs-lookup"><span data-stu-id="d4800-140">Surface magnetism</span></span>](surface-magnetism.md)
