---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699290"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="05063-104">Unreal のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="05063-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="05063-105">概要</span><span class="sxs-lookup"><span data-stu-id="05063-105">Overview</span></span>

<span data-ttu-id="05063-106">この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine に固有の学習に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="05063-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="05063-107">続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="05063-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="05063-108">推奨される Unreal プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="05063-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="05063-109">以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。</span><span class="sxs-lookup"><span data-stu-id="05063-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="05063-110">Mobile VR レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="05063-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="05063-111">**[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="05063-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="05063-113">前方レンダラーの使用:</span><span class="sxs-lookup"><span data-stu-id="05063-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="05063-114">Mixed Reality には、既定の遅延レンダリング パイプラインよりもこの機能の方がはるかに適しています。</span><span class="sxs-lookup"><span data-stu-id="05063-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="05063-115">その理由は主に、個別にオフにできる機能の数にあります。</span><span class="sxs-lookup"><span data-stu-id="05063-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="05063-116">詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05063-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![前方レンダリング](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="05063-118">頂点フォグの無効化:</span><span class="sxs-lookup"><span data-stu-id="05063-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="05063-119">頂点フォグでは、多角形の各頂点にフォグ計算を適用し、その結果を多角形の面全体で補間します。</span><span class="sxs-lookup"><span data-stu-id="05063-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="05063-120">ゲームでフォグを使用しない場合は、この設定を選択してフォグを無効にし、シェーディングのパフォーマンスを向上させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="05063-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![頂点フォグのオプション](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="05063-122">オクルージョン カリングの無効化:</span><span class="sxs-lookup"><span data-stu-id="05063-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="05063-123">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="05063-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="05063-124">レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="05063-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="05063-125">これにより、Unreal の作業は CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。</span><span class="sxs-lookup"><span data-stu-id="05063-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="05063-126">モバイル デバイスの GPU でオクルージョン カリングを行うと処理速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="05063-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="05063-127">一般に、GPU では主にレンダリングを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="05063-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="05063-128">オクルージョンによってパフォーマンスが向上すると思われる場合は、代わりにソフトウェア オクルージョンを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="05063-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="05063-129">多数の描画呼び出しによって既に CPU の負荷が大きくなっている場合、ソフトウェア オクルージョンを有効にするとパフォーマンスが低下する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="05063-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![オクルージョン カリングの無効化](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="05063-131">深度ステンシルの無効化:</span><span class="sxs-lookup"><span data-stu-id="05063-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="05063-132">この機能には追加のパスが必要になるため、処理速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="05063-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="05063-133">Unreal では、透明度を使用した場合も処理が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="05063-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="05063-134">詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05063-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![深度ステンシル](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="05063-136">モバイル マルチビューの使用:</span><span class="sxs-lookup"><span data-stu-id="05063-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="05063-137">**[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。</span><span class="sxs-lookup"><span data-stu-id="05063-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="05063-138">モバイル HDR をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="05063-138">Mobile HDR should be unchecked.</span></span>

![VR レンダリング設定](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="05063-140">カスケードされたシャドウ マップの削減:</span><span class="sxs-lookup"><span data-stu-id="05063-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="05063-141">シャドウ マップの数を減らすと、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="05063-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="05063-142">明らかに品質が低下しない限り、一般にこれは 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05063-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![カスケードされたシャドウ マップ](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="05063-144">オプション設定</span><span class="sxs-lookup"><span data-stu-id="05063-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="05063-145">次の設定を行うとパフォーマンスが向上する可能性がありますが、代わりに特定の機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="05063-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="05063-146">該当する機能が不要な場合にのみ、これらの設定を使用してください。</span><span class="sxs-lookup"><span data-stu-id="05063-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="05063-147">モバイル シェーダーの順列の削減</span><span class="sxs-lookup"><span data-stu-id="05063-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="05063-148">ライトがカメラとは無関係に移動しない場合は、この値を問題なく 0 に設定できます。</span><span class="sxs-lookup"><span data-stu-id="05063-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="05063-149">主な利点は、Unreal で複数のシェーダー順列をカリングし、シェーダーのコンパイルを高速化できることです。</span><span class="sxs-lookup"><span data-stu-id="05063-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![モバイル シェーダーの順列の削減](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="05063-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="05063-151">See also</span></span>
* [<span data-ttu-id="05063-152">Unreal Engine モバイルのパフォーマンス ガイドライン</span><span class="sxs-lookup"><span data-stu-id="05063-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)