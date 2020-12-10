---
title: Unity のカメラ
description: Windows Mixed Reality 開発に Unity のメインカメラを使用して holographic のレンダリングを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、holographic レンダリング、holographic、イマーシブ、フォーカスポイント、深度バッファー、方向専用、位置指定、不透明、透明、クリップ、混合 reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: 26eb8966004c958c6063d09de891ef835d973a82
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010433"
---
# <a name="camera-in-unity"></a><span data-ttu-id="32674-104">Unity のカメラ</span><span class="sxs-lookup"><span data-stu-id="32674-104">Camera in Unity</span></span>

<span data-ttu-id="32674-105">Mixed reality ヘッドセットを使用すると、holographic 世界の中心になります。</span><span class="sxs-lookup"><span data-stu-id="32674-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="32674-106">Unity [カメラ](https://docs.unity3d.com/Manual/class-Camera.html) コンポーネントは、ステレオスコピックのレンダリングを自動的に処理し、ヘッドの動きと回転に従います。</span><span class="sxs-lookup"><span data-stu-id="32674-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="32674-107">ただし、ビジュアルの品質とホログラムの [安定性](../platform-capabilities-and-apis/hologram-stability.md)を完全に最適化するには、以下で説明するカメラの設定を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32674-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="setup"></a><span data-ttu-id="32674-108">セットアップ</span><span class="sxs-lookup"><span data-stu-id="32674-108">Setup</span></span>

1. <span data-ttu-id="32674-109">**Windows ストアプレーヤー設定** の [**その他の設定**] セクションに進む</span><span class="sxs-lookup"><span data-stu-id="32674-109">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="32674-110">Windows **Mixed Reality** をデバイスとして選択します。これは、以前のバージョンの Unity では **windows Holographic** として一覧表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="32674-110">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="32674-111">**サポートされている仮想現実** を選択</span><span class="sxs-lookup"><span data-stu-id="32674-111">Select **Virtual Reality Supported**</span></span>

>[!NOTE]
><span data-ttu-id="32674-112">これらの設定は、アプリの各シーンのカメラに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32674-112">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="32674-113">既定では、Unity で新しいシーンを作成すると、カメラコンポーネントを含むメインのカメラのユーザーオブジェクトが階層に含まれますが、次の設定は適切に適用されません。</span><span class="sxs-lookup"><span data-stu-id="32674-113">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="32674-114">Holographic とイマーシブヘッドセット</span><span class="sxs-lookup"><span data-stu-id="32674-114">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="32674-115">Unity カメラコンポーネントの既定の設定は、従来の3D アプリケーション用です。実際の環境がないため、スカイボックスのような背景が必要です。</span><span class="sxs-lookup"><span data-stu-id="32674-115">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="32674-116">**[イマーシブヘッドセット](../../discover/immersive-headset-hardware-details.md)** で実行すると、ユーザーに表示されるすべてのものが表示されるため、スカイボックスを保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="32674-116">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="32674-117">ただし、 [HoloLens](../../hololens-hardware-details.md)などの **holographic ヘッドセット** で実行する場合、カメラがレンダリングするすべての要素の背後に実際の世界が表示されます。</span><span class="sxs-lookup"><span data-stu-id="32674-117">However, when running on a **holographic headset** like [HoloLens](../../hololens-hardware-details.md), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="32674-118">スカイボックステクスチャの代わりに、カメラの背景を透明に設定します (HoloLens では、黒は透明としてレンダリングされます)。</span><span class="sxs-lookup"><span data-stu-id="32674-118">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="32674-119">[階層] パネルでメインカメラを選択します。</span><span class="sxs-lookup"><span data-stu-id="32674-119">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="32674-120">[インスペクター] パネルでカメラコンポーネントを見つけて、[クリアフラグ] ドロップダウンを [スカイボックス] から [純色] に変更します。</span><span class="sxs-lookup"><span data-stu-id="32674-120">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="32674-121">背景色ピッカーを選択し、RGBA 値を (0, 0, 0, 0) に変更します。</span><span class="sxs-lookup"><span data-stu-id="32674-121">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="32674-122">スクリプトコードを使用して、HolographicSettings をチェックすることによって、ヘッドセットがイマーシブであるか holographic であるかを実行時に判断することができ[ます。](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)</span><span class="sxs-lookup"><span data-stu-id="32674-122">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>

## <a name="positioning-the-camera"></a><span data-ttu-id="32674-123">カメラの配置</span><span class="sxs-lookup"><span data-stu-id="32674-123">Positioning the Camera</span></span>

<span data-ttu-id="32674-124">ユーザーの開始位置を (X: 0, Y: 0, Z: 0) と考えると、アプリのレイアウトが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="32674-124">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="32674-125">メインカメラはユーザーのヘッドの移動を追跡しているため、ユーザーの開始位置を設定することによって、メインカメラの開始位置を設定できます。</span><span class="sxs-lookup"><span data-stu-id="32674-125">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="32674-126">[階層] パネルの [メインカメラ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="32674-126">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="32674-127">[インスペクター] パネルで変換コンポーネントを見つけ、位置を (X: 0, Y: 1, Z:-10) から (X: 0, Y: 0, Z: 0) に変更します。</span><span class="sxs-lookup"><span data-stu-id="32674-127">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="32674-128">![Unity の [インスペクター] ウィンドウの [カメラ]](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="32674-128">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="32674-129">*Unity の [インスペクター] ウィンドウの [カメラ]*</span><span class="sxs-lookup"><span data-stu-id="32674-129">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="32674-130">クリッププレーン</span><span class="sxs-lookup"><span data-stu-id="32674-130">Clip planes</span></span>

<span data-ttu-id="32674-131">ユーザーに近いコンテンツのレンダリングは、mixed reality で不快に感じられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32674-131">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="32674-132">カメラコンポーネントでは、 [近距離と遠くのクリップ平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) を調整できます。</span><span class="sxs-lookup"><span data-stu-id="32674-132">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="32674-133">[階層] パネルでメインカメラを選択します。</span><span class="sxs-lookup"><span data-stu-id="32674-133">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="32674-134">[インスペクター] パネルでカメラコンポーネントのクリッピング平面を見つけ、[Near] ボックスを0.3 から0.85 に変更します。</span><span class="sxs-lookup"><span data-stu-id="32674-134">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to 0.85.</span></span> <span data-ttu-id="32674-135">さらに近いコンテンツは、ユーザーの不快感につながる可能性があります。 [レンダリング距離のガイドライン](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)に従って回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32674-135">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="32674-136">複数のカメラ</span><span class="sxs-lookup"><span data-stu-id="32674-136">Multiple Cameras</span></span>

<span data-ttu-id="32674-137">シーンに複数のカメラコンポーネントがある場合、Unity は、どのステレオスコピックオブジェクトに MainCamera タグがあるかに基づいて、レンダリングとヘッドトラッキングに使用するカメラを認識します。</span><span class="sxs-lookup"><span data-stu-id="32674-137">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking based on which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="32674-138">装着済みエクスペリエンスを入力する</span><span class="sxs-lookup"><span data-stu-id="32674-138">Recentering a seated experience</span></span>

<span data-ttu-id="32674-139">[固定スケールのエクスペリエンス](../../design/coordinate-systems.md)を構築している場合は、XR を呼び出すことによって、ユーザーの現在の位置に Unity の recenter を持たせることができ **[ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** メソッド。</span><span class="sxs-lookup"><span data-stu-id="32674-139">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="32674-140">再プロジェクションモード</span><span class="sxs-lookup"><span data-stu-id="32674-140">Reprojection modes</span></span>

<span data-ttu-id="32674-141">HoloLens とイマーシブヘッドセットはどちらも、photons が出力されたときにユーザーの実際のヘッド位置の misprediction を調整するために、アプリがレンダリングする各フレームを再プロジェクトします。</span><span class="sxs-lookup"><span data-stu-id="32674-141">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="32674-142">既定では:</span><span class="sxs-lookup"><span data-stu-id="32674-142">By default:</span></span>

* <span data-ttu-id="32674-143">アプリが特定のフレームに対して深度バッファーを提供する場合、**イマーシブヘッドセット** は位置指定リポジトリを処理します。</span><span class="sxs-lookup"><span data-stu-id="32674-143">**Immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="32674-144">また、イマーシブヘッドセットは、位置と向きの両方で misprediction のホログラムを調整します。</span><span class="sxs-lookup"><span data-stu-id="32674-144">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="32674-145">深度バッファーが指定されていない場合、システムは mispredictions の向きのみを修正します。</span><span class="sxs-lookup"><span data-stu-id="32674-145">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="32674-146">HoloLens のような **Holographic ヘッドセット** は、アプリが深度バッファーを提供するかどうかに関係なく、位置指定リポジトリを処理します。</span><span class="sxs-lookup"><span data-stu-id="32674-146">**Holographic headsets** like HoloLens will take care of positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="32674-147">レンダリングは、実際には安定した背景でスパースになることが多いため、HoloLens で深度バッファーを使用せずに位置指定リポジトリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="32674-147">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="32674-148">固定本文でロックされたコンテンツ (たとえば、360度のビデオコンテンツ) を使用して[向きのみのエクスペリエンス](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)を構築していることがわかっている場合は、HolographicSettings を[HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)に設定することによってのみ、Reprojection モードを[ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)に明示的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="32674-148">If you know that you're building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="32674-149">Windows での深度バッファーの共有</span><span class="sxs-lookup"><span data-stu-id="32674-149">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="32674-150">アプリの深度バッファーを Windows に共有すると、アプリは、レンダリングするヘッドセットの種類に基づいて、ホログラムの安定性の2つのブーストのうちの1つを提供します。</span><span class="sxs-lookup"><span data-stu-id="32674-150">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="32674-151">**イマーシブヘッドセット** は、深度バッファーが提供されたときに位置指定再投影を処理し、位置と向きの両方で misprediction のホログラムを調整します。</span><span class="sxs-lookup"><span data-stu-id="32674-151">**Immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="32674-152">**Holographic ヘッドセット** には、いくつかの異なる方法があります。</span><span class="sxs-lookup"><span data-stu-id="32674-152">**Holographic headsets** have a few different methods.</span></span> <span data-ttu-id="32674-153">HoloLens 1 は、深度バッファーが指定されると自動的に [フォーカスポイント](focus-point-in-unity.md) を選択し、ほとんどのコンテンツと交差する平面に沿ったホログラムの安定性を最適化します。</span><span class="sxs-lookup"><span data-stu-id="32674-153">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="32674-154">HoloLens 2 は、Depth LSR を使用してコンテンツを安定化します [(「解説」を参照してください)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。</span><span class="sxs-lookup"><span data-stu-id="32674-154">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

<span data-ttu-id="32674-155">Unity アプリで Windows に深度バッファーを提供するかどうかを設定するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="32674-155">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="32674-156">[ **Edit**  >  **Project settings**  >  **Player**  >  **] ユニバーサル Windows プラットフォーム tab**  >  **XR settings**] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="32674-156">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="32674-157">[ **Windows Mixed REALITY SDK** ] 項目を展開します。</span><span class="sxs-lookup"><span data-stu-id="32674-157">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="32674-158">[ **深度バッファーの共有を有効にする** ] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="32674-158">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="32674-159">新しいプロジェクトでは、[深度バッファーの共有を有効にする] が既定でオンになっています。これは、この機能が Unity に追加され、アップグレードされた古いプロジェクトに対して既定ではオフになるためです。</span><span class="sxs-lookup"><span data-stu-id="32674-159">Enable Depth Buffer Sharing is checked by default in new projects, since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="32674-160">深度バッファーを使用すると、メインカメラで Unity に設定した近距離および遠面を使用して、深度バッファーの正規化されたピクセルごとの深度値をメートル単位の距離に正確にマップできます。</span><span class="sxs-lookup"><span data-stu-id="32674-160">A depth buffer can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="32674-161">通常の方法でレンダリングがハンドルの深さの値を渡す場合は、通常、ここで問題ありません。ただし、既存のカラーピクセルに対してを使用している間に深度バッファーに書き込む半透明のレンダリングパスは、再プロジェクションを混乱させる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32674-161">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="32674-162">レンダリングパスによって、最終的な深度ピクセルの多くが正確でない深さの値になることがわかっている場合は、[深度バッファーの共有を有効にする] をオフにすると、表示品質が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32674-162">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a><span data-ttu-id="32674-163">混合 Reality ツールキットを使用した自動シーンおよびカメラ設定</span><span class="sxs-lookup"><span data-stu-id="32674-163">Automatic Scene and Camera Setup with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="32674-164">ステップ [バイステップ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ガイドに従って Unity プロジェクトに Mixed Reality Toolkit を追加すると、プロジェクトが自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="32674-164">Follow the [step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) guide to add Mixed Reality Toolkit to your Unity project and it will configure your project automatically.</span></span> <span data-ttu-id="32674-165">また、次のセクションのガイドを使用して、MRTK なしでプロジェクトを手動で構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="32674-165">You can also manually configure the project without MRTK with the guide in the section below.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="32674-166">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="32674-166">Next Development Checkpoint</span></span>

<span data-ttu-id="32674-167">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="32674-167">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="32674-168">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="32674-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="32674-169">視線入力</span><span class="sxs-lookup"><span data-stu-id="32674-169">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="32674-170">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="32674-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="32674-171">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="32674-171">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="32674-172">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="32674-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="32674-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="32674-173">See also</span></span>

* [<span data-ttu-id="32674-174">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="32674-174">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="32674-175">MixedRealityToolkit メインカメラ。 prefab</span><span class="sxs-lookup"><span data-stu-id="32674-175">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
