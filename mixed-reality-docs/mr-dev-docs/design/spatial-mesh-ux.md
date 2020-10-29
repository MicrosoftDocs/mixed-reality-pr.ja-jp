---
title: 空間メッシュの視覚化
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality、HoloLens、UI コントロール、相互作用、ui、ux、UX デザイン、空間 UI、空間相互作用、3D UI、3D UX
ms.openlocfilehash: 2c811edc14fbcc7c917fe9fa724f1cab23179a96
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686090"
---
# <a name="spatial-mesh"></a><span data-ttu-id="15177-103">空間メッシュ</span><span class="sxs-lookup"><span data-stu-id="15177-103">Spatial mesh</span></span>

![空間メッシュ](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="15177-105">ユーザーは、空間メッシュの視覚エフェクトを使用して、デバイスがどのように物理的な環境を認識し、理解しているかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="15177-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="15177-106">空間コンテキストを提供するだけでなく、適切な空間メッシュの視覚化によって、すばらしいと魔法のエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="15177-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="15177-107">設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="15177-107">Design guideline</span></span>
<span data-ttu-id="15177-108">ユーザーがコンテンツにフォーカスを設定して操作できるようにすることが重要であるため、バックグラウンドで空間メッシュを連続して繰り返し表示することは困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15177-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="15177-109">最初の起動時に1回だけ環境を表示しないようにするか、またはユーザーがスペースをターゲットにして環境メッシュを表示する明確な意図を示すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="15177-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="15177-110">HoloLens シェルでは、この動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="15177-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="15177-111">Unity 用の MRTK (Mixed Reality Toolkit) での空間メッシュの視覚化</span><span class="sxs-lookup"><span data-stu-id="15177-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="15177-112">MRTK には、空間メッシュの視覚化に関するいくつかの素材が用意されています。</span><span class="sxs-lookup"><span data-stu-id="15177-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="15177-113">**MRTK_Wireframe、MRTK_Wireframe ます** 。既定の静的な空間メッシュマテリアルは、アニメーションを使用せずにメッシュのアウトラインを示します。</span><span class="sxs-lookup"><span data-stu-id="15177-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat** : Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="15177-114">この資料は、空間メッシュジオメトリ全体を示すため、デバッグのために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15177-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="15177-115">ただし、運用環境では推奨されません。</span><span class="sxs-lookup"><span data-stu-id="15177-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="15177-116">**MRTK_SurfaceReconstruction** : この資料では、空間メッシュにアニメーション化されたパルス効果を提供します。</span><span class="sxs-lookup"><span data-stu-id="15177-116">**MRTK_SurfaceReconstruction.mat** : This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="15177-117">このマテリアルを使用して、特定の時点で、またはユーザーのエアタップ入力で環境を視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="15177-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="15177-118">例については、「 **PulseShaderExamples** シーン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15177-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="15177-119">詳細については、「 [Mrtk-空間認識](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 」と「 [Mrtk-Pulse シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15177-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="15177-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="15177-120">See also</span></span>

* [<span data-ttu-id="15177-121">カーソル</span><span class="sxs-lookup"><span data-stu-id="15177-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="15177-122">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="15177-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="15177-123">ボタン</span><span class="sxs-lookup"><span data-stu-id="15177-123">Button</span></span>](button.md)
* [<span data-ttu-id="15177-124">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="15177-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="15177-125">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="15177-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="15177-126">操作</span><span class="sxs-lookup"><span data-stu-id="15177-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="15177-127">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="15177-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="15177-128">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="15177-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="15177-129">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="15177-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="15177-130">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="15177-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="15177-131">キーボード</span><span class="sxs-lookup"><span data-stu-id="15177-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="15177-132">ヒント</span><span class="sxs-lookup"><span data-stu-id="15177-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="15177-133">スレート</span><span class="sxs-lookup"><span data-stu-id="15177-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="15177-134">スライダー</span><span class="sxs-lookup"><span data-stu-id="15177-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="15177-135">シェーダー</span><span class="sxs-lookup"><span data-stu-id="15177-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="15177-136">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="15177-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="15177-137">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="15177-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="15177-138">表面吸着</span><span class="sxs-lookup"><span data-stu-id="15177-138">Surface magnetism</span></span>](surface-magnetism.md)
