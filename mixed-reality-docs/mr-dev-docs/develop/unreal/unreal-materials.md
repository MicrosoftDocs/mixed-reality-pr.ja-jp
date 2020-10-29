---
title: Unreal のマテリアルに関する推奨事項
description: Unreal engine のマテリアルの概要。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開発、マテリアル、ドキュメント、ガイド、特徴、ホログラム、ゲーム開発
ms.openlocfilehash: bfce6e6bf8acd58821dba1213e1f1ab571d85a0c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684546"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="f5a65-104">Unreal のマテリアルに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="f5a65-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="f5a65-105">Unreal Engine では、マテリアルはパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="f5a65-106">このページは、最高のパフォーマンスを得るために使用する必要がある基本設定のクイックスタートとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="f5a65-107">CustomizedUVs の使用</span><span class="sxs-lookup"><span data-stu-id="f5a65-107">Using CustomizedUVs</span></span>

<span data-ttu-id="f5a65-108">素材に UVs のタイルを提供する必要がある場合は、テクスチャノードの UV を直接変更するのではなく、CustomizedUVs を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="f5a65-109">CustomizedUVs は、ピクセルシェーダーではなく頂点シェーダーで UV 操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f5a65-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Unreal のマテリアル設定](images/unreal-materials-img-01c.png)

<span data-ttu-id="f5a65-111">素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) と、次のスクリーンショットのベストプラクティスの例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="f5a65-112">推奨される[ ![ 未 ](images/unreal-materials-img-01.png) 設定の資料での推奨資料の設定](images/unreal-materials-img-01.png#lightbox) 
 *Recommended material setup*</span><span class="sxs-lookup"><span data-stu-id="f5a65-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="f5a65-113">推奨される[ ![ unreal ](images/unreal-materials-img-01b.png) 以外のマテリアルのセットアップでの推奨されるマテリアル以外の設定](images/unreal-materials-img-01b.png#lightbox) 
 *Non-recommended material setup*</span><span class="sxs-lookup"><span data-stu-id="f5a65-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="f5a65-114">Blend モードの変更</span><span class="sxs-lookup"><span data-stu-id="f5a65-114">Changing Blend Mode</span></span>

<span data-ttu-id="f5a65-115">特に複雑な理由がない限り、blend モードを不透明に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="f5a65-116">マスクされた半透明な素材は低速です。</span><span class="sxs-lookup"><span data-stu-id="f5a65-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="f5a65-117">素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Blend モードの変更](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="f5a65-119">モバイルのライティングを更新しています</span><span class="sxs-lookup"><span data-stu-id="f5a65-119">Updating lighting for mobile</span></span>

<span data-ttu-id="f5a65-120">完全有効桁数はオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-120">Full precision should be turned off.</span></span> <span data-ttu-id="f5a65-121">ライトマップライトは、方向情報を有効にすることで、ダイヤルダウンできます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="f5a65-122">無効にすると、ライトマップからの光源は平坦になりますが、コストは安くなります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Unreal のモバイルマテリアル設定](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="f5a65-124">前方シェーディングの調整</span><span class="sxs-lookup"><span data-stu-id="f5a65-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="f5a65-125">これらのオプションを選択すると、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="f5a65-126">パフォーマンスを最大にするためにオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-126">They should be turned off for maximum performance.</span></span>

![Unreal の事前シェーディングマテリアル設定](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="f5a65-128">素材の透明度の設定</span><span class="sxs-lookup"><span data-stu-id="f5a65-128">Setting material translucency</span></span>

<span data-ttu-id="f5a65-129">半透明のマテリアルがブルームまたは自由度の影響を受けないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="f5a65-130">MR では両方の影響がまれであるため、この設定は既定でオンになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![モバイル分離の透明度設定 (Unreal)](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="f5a65-132">オプション設定</span><span class="sxs-lookup"><span data-stu-id="f5a65-132">Optional settings</span></span>

<span data-ttu-id="f5a65-133">次の設定では、パフォーマンスが向上する場合がありますが、特定の機能が無効になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="f5a65-134">問題の機能を必要としない場合にのみ、これらの設定を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Unreal のオプションのマテリアル設定](images/unreal-materials-img-06.jpg)

<span data-ttu-id="f5a65-136">マテリアルに反射や光が不要な場合は、このオプションを設定するとパフォーマンスが大幅に向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="f5a65-137">内部テストでは、照明情報を提供すると同時に "unlit" の速度になります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f5a65-138">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f5a65-138">Best practices</span></span>

<span data-ttu-id="f5a65-139">以下は、資料に関連するベストプラクティスであるため、"設定" ではありません。</span><span class="sxs-lookup"><span data-stu-id="f5a65-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="f5a65-140">パラメーターを作成するときは、可能な限り "静的パラメーター" を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f5a65-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="f5a65-141">静的スイッチを使用すると、実行時のコストを発生させずに、素材の分岐全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="f5a65-142">インスタンスは異なる値を持つことができるため、テンプレート化されたシェーダーを設定し、パフォーマンスを低下させることはできません。</span><span class="sxs-lookup"><span data-stu-id="f5a65-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="f5a65-143">ただし、これによって多くの順列が生成されるため、多くのシェーダーの再コンパイルが発生します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="f5a65-144">マテリアル内の静的なパラメーターの数と、実際に使用される静的パラメーターの順列の数を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="f5a65-145">レンダリングマテリアルのパラメーターの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![マテリアル設定のベストプラクティス](images/unreal-materials-img-07.jpg)

<span data-ttu-id="f5a65-147">素材のインスタンスを作成するときは、マテリアルインスタンスの **定数** を動的に使用するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="f5a65-148">**Material Instance Constant** は、ランタイムの前に1回だけ計算する、インスタンス化された素材です。</span><span class="sxs-lookup"><span data-stu-id="f5a65-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="f5a65-149">コンテンツブラウザーを使用して作成された素材インスタンス ( **右クリック > Create Material instance** ) は、素材インスタンス定数です。</span><span class="sxs-lookup"><span data-stu-id="f5a65-149">The material instance created via the Content Browser ( **right-click > Create Material Instance** ) is a Material Instance Constant.</span></span> <span data-ttu-id="f5a65-150">マテリアルインスタンス動的は、コードを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="f5a65-151">マテリアルインスタンスの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Unreal での素材インスタンスの作成](images/unreal-materials-img-08.png)

<span data-ttu-id="f5a65-153">素材/シェーダーの複雑さに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="f5a65-154">[プラットフォームの統計] アイコンをクリックすると、さまざまなプラットフォームでの素材のコストを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="f5a65-155">素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Unreal での素材インスタンス動的設定の作成](images/unreal-materials-img-09.png)

<span data-ttu-id="f5a65-157">シェーダーの複雑さの [表示モード](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)を使用して、シェーダーの相対的な複雑さを簡単に把握できます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="f5a65-158">表示モードホットキー: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="f5a65-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="f5a65-159">コンソールコマンド: viewmode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="f5a65-159">Console command: viewmode shadercomplexity</span></span>

![Unreal の素材の複雑さ](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="f5a65-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5a65-161">See also</span></span>
* [<span data-ttu-id="f5a65-162">モバイル資料</span><span class="sxs-lookup"><span data-stu-id="f5a65-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="f5a65-163">表示モード</span><span class="sxs-lookup"><span data-stu-id="f5a65-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="f5a65-164">素材のインスタンス</span><span class="sxs-lookup"><span data-stu-id="f5a65-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
