---
title: Unreal のパフォーマンスに関する推奨事項
description: 推奨される Unreal プロジェクトの設定を使用して、Mixed Reality アプリから最高のパフォーマンスを引き出す方法について説明します。
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583064"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="064e4-104">Unreal のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="064e4-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="064e4-105">Unreal Engine が備える、アプリのパフォーマンス向上につながるいくつかの機能はすべて、[Mixed Reality のパフォーマンスに関する推奨事項](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)に関するページで概要が示されている検討内容に基づいています。</span><span class="sxs-lookup"><span data-stu-id="064e4-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="064e4-106">続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="064e4-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="064e4-107">推奨される Unreal プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="064e4-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="064e4-108">以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。</span><span class="sxs-lookup"><span data-stu-id="064e4-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="064e4-109">Mobile VR レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="064e4-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="064e4-110">**[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="064e4-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="064e4-112">前方レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="064e4-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="064e4-113">前方レンダラーは、個別にオフにできる機能の数のため、既定の遅延レンダリング パイプラインより Mixed Reality にいっそう適しています。</span><span class="sxs-lookup"><span data-stu-id="064e4-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="064e4-114">詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="064e4-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![前方レンダリング](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="064e4-116">モバイル マルチビューの使用:</span><span class="sxs-lookup"><span data-stu-id="064e4-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="064e4-117">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。</span><span class="sxs-lookup"><span data-stu-id="064e4-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="064e4-118">モバイル HDR をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="064e4-118">Mobile HDR should be unchecked.</span></span>

![VR レンダリング設定](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="064e4-120">**[OpenXR only]\(OpenXR のみ\)** **[Default RHI]\(既定の RHI\)** で **[Default]\(既定\)** または **[D3D12]** が選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="064e4-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="064e4-121">**D3D11** を選択すると、プラットフォームで追加のレンダー パスが実行されるため、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="064e4-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="064e4-122">**D3D12** では、追加のレンダー パスが回避され、レンダリング パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="064e4-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![既定の RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="064e4-124">頂点フォグの無効化:</span><span class="sxs-lookup"><span data-stu-id="064e4-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="064e4-125">頂点フォグでは、多角形の各頂点にフォグ計算を適用し、その結果を多角形の面全体で補間します。</span><span class="sxs-lookup"><span data-stu-id="064e4-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="064e4-126">ゲームでフォグを使用しない場合は、頂点フォグを無効にして、シェーディング パフォーマンスを向上させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="064e4-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![頂点フォグのオプション](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="064e4-128">オクルージョン カリングの無効化:</span><span class="sxs-lookup"><span data-stu-id="064e4-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="064e4-129">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="064e4-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="064e4-130">レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="064e4-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="064e4-131">Unreal により、CPU 上で処理が実行されて、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリが回避されます。</span><span class="sxs-lookup"><span data-stu-id="064e4-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="064e4-132">モバイル デバイスの GPU でオクルージョン カリングを行うと処理速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="064e4-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="064e4-133">一般に、GPU では主にレンダリングを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="064e4-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="064e4-134">オクルージョンによってパフォーマンスが向上すると思われる場合は、代わりにソフトウェア オクルージョンを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="064e4-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="064e4-135">多数の描画呼び出しによって既に CPU の負荷が大きくなっている場合、ソフトウェア オクルージョンを有効にするとパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="064e4-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![オクルージョン カリングの無効化](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="064e4-137">カスタム深度ステンシル パスの無効化:</span><span class="sxs-lookup"><span data-stu-id="064e4-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="064e4-138">カスタム深度を無効にすると、余分なパスが必要になり、結果として処理が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="064e4-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="064e4-139">Unreal では、透明度を使用した場合も処理が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="064e4-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="064e4-140">詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="064e4-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![深度ステンシル](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="064e4-142">カスケードされたシャドウ マップの削減:</span><span class="sxs-lookup"><span data-stu-id="064e4-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="064e4-143">シャドウ マップの数を減らすと、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="064e4-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="064e4-144">一般に、目に見えて品質が低下しない限り、プロパティを 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="064e4-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![カスケードされたシャドウ マップ](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="064e4-146">オプション設定</span><span class="sxs-lookup"><span data-stu-id="064e4-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="064e4-147">次の設定を行うとパフォーマンスが向上する可能性がありますが、代わりに特定の機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="064e4-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="064e4-148">該当する機能が不要な場合にのみ、これらの設定を使用してください。</span><span class="sxs-lookup"><span data-stu-id="064e4-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="064e4-149">モバイル シェーダーの順列の削減</span><span class="sxs-lookup"><span data-stu-id="064e4-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="064e4-150">ライトがカメラとは無関係に移動しない場合は、プロパティの値を問題なく 0 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="064e4-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="064e4-151">主な利点は、Unreal で複数のシェーダー順列をカリングし、シェーダーのコンパイルを高速化できることです。</span><span class="sxs-lookup"><span data-stu-id="064e4-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![モバイル シェーダーの順列の削減](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="064e4-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="064e4-153">See also</span></span>

* [<span data-ttu-id="064e4-154">Unreal Engine モバイルのパフォーマンス ガイドライン</span><span class="sxs-lookup"><span data-stu-id="064e4-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)