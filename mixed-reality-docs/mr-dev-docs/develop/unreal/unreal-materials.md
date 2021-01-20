---
title: Unreal の素材に関する推奨事項
description: Unreal engine のマテリアルの概要。
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開発、マテリアル、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: bfe70e730c5fbd6e5d103737b03e76bfd0ab65f6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580798"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="9039b-104">Unreal の素材に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9039b-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="9039b-105">使用する素材は、Unreal Engine でのプロジェクトの実行がどの程度適切であるかに直接影響します。</span><span class="sxs-lookup"><span data-stu-id="9039b-105">The materials you use can directly affect how well your projects run in Unreal Engine.</span></span> <span data-ttu-id="9039b-106">このページは、混合現実アプリケーションから最適なパフォーマンスを得るために使用する必要がある基本設定のクイックスタートとして機能します。</span><span class="sxs-lookup"><span data-stu-id="9039b-106">This page acts as a quick-start for the basic settings you should be using to get the best performance out of your mixed reality applications.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="9039b-107">CustomizedUVs の使用</span><span class="sxs-lookup"><span data-stu-id="9039b-107">Using CustomizedUVs</span></span>

<span data-ttu-id="9039b-108">素材に UV タイルを提供する必要がある場合は、テクスチャノードの UV を直接変更するのではなく、CustomizedUVs を使用します。</span><span class="sxs-lookup"><span data-stu-id="9039b-108">If you need to provide UV tiling on your material, use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="9039b-109">CustomizedUVs を使用すると、ピクセルシェーダーではなく、頂点シェーダーで UVs を操作できます。</span><span class="sxs-lookup"><span data-stu-id="9039b-109">CustomizedUVs let you manipulate UVs in the Vertex shaders rather than the Pixel shader.</span></span>

![Unreal のマテリアル設定](images/unreal-materials-img-01c.png)

<span data-ttu-id="9039b-111">素材の詳細については、次のスクリーンショットの [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) とベストプラクティスの例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-111">You can find material details in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="9039b-112">推奨される[ ![ 未 ](images/unreal-materials-img-01.png) 設定の資料での推奨資料の設定](images/unreal-materials-img-01.png#lightbox) 
 </span><span class="sxs-lookup"><span data-stu-id="9039b-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="9039b-113">推奨される[ ![ unreal ](images/unreal-materials-img-01b.png) 以外のマテリアルのセットアップでの推奨されるマテリアル以外の設定](images/unreal-materials-img-01b.png#lightbox) 
 </span><span class="sxs-lookup"><span data-stu-id="9039b-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="9039b-114">Blend モードの変更</span><span class="sxs-lookup"><span data-stu-id="9039b-114">Changing Blend Mode</span></span>

<span data-ttu-id="9039b-115">特に複雑な理由がない限り、blend モードを不透明に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9039b-115">We recommend setting the blend mode to opaque unless there's a strong reason to do otherwise.</span></span> <span data-ttu-id="9039b-116">マスクされた半透明な素材は低速です。</span><span class="sxs-lookup"><span data-stu-id="9039b-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="9039b-117">素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Blend モードの変更](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="9039b-119">モバイルのライティングを更新しています</span><span class="sxs-lookup"><span data-stu-id="9039b-119">Updating lighting for mobile</span></span>

<span data-ttu-id="9039b-120">完全有効桁数はオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9039b-120">Full precision should be turned off.</span></span> <span data-ttu-id="9039b-121">ライトマップライトは、方向情報を有効にすることで、ダイヤルダウンできます。</span><span class="sxs-lookup"><span data-stu-id="9039b-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="9039b-122">無効にすると、ライトマップからの光源は平坦になりますが、コストは安くなります。</span><span class="sxs-lookup"><span data-stu-id="9039b-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Unreal のモバイルマテリアル設定](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="9039b-124">前方シェーディングの調整</span><span class="sxs-lookup"><span data-stu-id="9039b-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="9039b-125">これらのオプションを選択すると、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="9039b-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="9039b-126">パフォーマンスを最大にするためにオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9039b-126">They should be turned off for maximum performance.</span></span>

![Unreal の事前シェーディングマテリアル設定](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="9039b-128">素材の透明度の設定</span><span class="sxs-lookup"><span data-stu-id="9039b-128">Setting material translucency</span></span>

<span data-ttu-id="9039b-129">半透明のマテリアルがブルームまたは自由度の影響を受けないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9039b-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="9039b-130">MR では両方の影響がまれであるため、この設定は既定でオンになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9039b-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![モバイル分離の透明度設定 (Unreal)](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="9039b-132">オプション設定</span><span class="sxs-lookup"><span data-stu-id="9039b-132">Optional settings</span></span>

<span data-ttu-id="9039b-133">次の設定では、パフォーマンスが向上する場合がありますが、特定の機能が無効になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="9039b-134">該当する機能が不要な場合にのみ、これらの設定を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-134">Only use these settings if you're sure you don't need the features in question.</span></span>

![Unreal のオプションのマテリアル設定](images/unreal-materials-img-06.jpg)

<span data-ttu-id="9039b-136">マテリアルに反射や光が不要な場合は、このオプションを設定するとパフォーマンスが大幅に向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9039b-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="9039b-137">内部テストでは、照明情報を提供しながら、"unlit" のように高速です。</span><span class="sxs-lookup"><span data-stu-id="9039b-137">In internal testing, it's as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="9039b-138">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="9039b-138">Best practices</span></span>

<span data-ttu-id="9039b-139">以下は、資料に関連するベストプラクティスであるため、"設定" ではありません。</span><span class="sxs-lookup"><span data-stu-id="9039b-139">The following aren't "settings" as much as they're best practices related to Materials.</span></span>

<span data-ttu-id="9039b-140">パラメーターを作成するときは、可能な限り "静的パラメーター" を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9039b-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="9039b-141">静的スイッチを使用すると、実行時のコストを発生させずに、素材の分岐全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="9039b-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="9039b-142">インスタンスは異なる値を持つことができるため、パフォーマンスが失われることなく、テンプレート化されたシェーダーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="9039b-142">Instances can have different values, making it possible to have a templated shader set up with no performance loss.</span></span> <span data-ttu-id="9039b-143">欠点は、シェーダーの再コンパイルの原因となるいくつかの順列が作成されることです。</span><span class="sxs-lookup"><span data-stu-id="9039b-143">The downside, is that several permutations are created that will cause shader recompilation.</span></span> <span data-ttu-id="9039b-144">マテリアル内の静的なパラメーターの数と、使用される静的パラメーターの順列の数を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="9039b-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are used.</span></span> <span data-ttu-id="9039b-145">レンダリングマテリアルのパラメーターの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![マテリアル設定のベストプラクティス](images/unreal-materials-img-07.jpg)

<span data-ttu-id="9039b-147">素材のインスタンスを作成するときは、マテリアルインスタンスの **定数** を動的に使用するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9039b-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="9039b-148">**Material Instance Constant** は、実行前に1回だけ計算する、インスタンス化された素材です。</span><span class="sxs-lookup"><span data-stu-id="9039b-148">**Material Instance Constant** is an instanced Material that calculates only once before runtime.</span></span>

<span data-ttu-id="9039b-149">コンテンツブラウザーを使用して作成された素材インスタンス (**右クリック > Create Material instance**) は、素材インスタンス定数です。</span><span class="sxs-lookup"><span data-stu-id="9039b-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="9039b-150">マテリアルインスタンス動的は、コードを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="9039b-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="9039b-151">マテリアルインスタンスの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Unreal での素材インスタンスの作成](images/unreal-materials-img-08.png)

<span data-ttu-id="9039b-153">素材/シェーダーの複雑さに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="9039b-154">[プラットフォームの統計] アイコンをクリックすると、さまざまなプラットフォームでの素材のコストを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9039b-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="9039b-155">素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9039b-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Unreal での素材インスタンス動的設定の作成](images/unreal-materials-img-09.png)

<span data-ttu-id="9039b-157">シェーダーの複雑さの [表示モード](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)を使用して、シェーダーの相対的な複雑さを簡単に把握できます。</span><span class="sxs-lookup"><span data-stu-id="9039b-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="9039b-158">表示モードホットキー: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="9039b-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="9039b-159">コンソールコマンド: viewmode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="9039b-159">Console command: viewmode shadercomplexity</span></span>

![Unreal の素材の複雑さ](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="9039b-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="9039b-161">See also</span></span>
* [<span data-ttu-id="9039b-162">モバイル資料</span><span class="sxs-lookup"><span data-stu-id="9039b-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="9039b-163">表示モード</span><span class="sxs-lookup"><span data-stu-id="9039b-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="9039b-164">素材のインスタンス</span><span class="sxs-lookup"><span data-stu-id="9039b-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
