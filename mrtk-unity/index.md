---
title: MRTK-Unity 開発者向けドキュメント
description: Unity 用 Mixed Reality Toolkit について説明します。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 開発, MRTK
ms.openlocfilehash: 3ac16a1aae6681ddd7e144679b76b4d2b778306f
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237253"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="e6bad-104">Mixed Reality Toolkit とは</span><span class="sxs-lookup"><span data-stu-id="e6bad-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality ツールキット](features/images/Logo_MRTK_Unity_Banner.png)

<span data-ttu-id="e6bad-106">MRTK-Unity は、一連のコンポーネントと機能を提供する Microsoft 主導のプロジェクトで、Unity でクロスプラットフォームの MR アプリの開発時間を短縮するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="e6bad-107">その機能の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-107">Here are some of its functions:</span></span>

* <span data-ttu-id="e6bad-108">**空間操作および UI 用のクロスプラットフォーム入力システムと構成要素** が提供されます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="e6bad-109">エディター内シミュレーションを通じて **プロトタイプの迅速な作成** を実現し、変更を即座に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e6bad-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="e6bad-110">開発者がコア コンポーネントを交換できる **拡張可能なフレームワーク** として動作します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="e6bad-111">次のような **幅広い範囲のプラットフォームをサポート** します</span><span class="sxs-lookup"><span data-stu-id="e6bad-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="e6bad-112">OpenXR (Unity 2020.2 以降)</span><span class="sxs-lookup"><span data-stu-id="e6bad-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="e6bad-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e6bad-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="e6bad-114">Windows Mixed Reality ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="e6bad-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="e6bad-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e6bad-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="e6bad-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="e6bad-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="e6bad-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e6bad-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="e6bad-118">Windows Mixed Reality ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="e6bad-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="e6bad-119">Oculus (Unity 2019.3 以降)</span><span class="sxs-lookup"><span data-stu-id="e6bad-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="e6bad-120">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="e6bad-120">Oculus Quest</span></span>
  * <span data-ttu-id="e6bad-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="e6bad-121">OpenVR</span></span>
    * <span data-ttu-id="e6bad-122">Windows Mixed Reality ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="e6bad-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="e6bad-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="e6bad-123">HTC Vive</span></span>
    * <span data-ttu-id="e6bad-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="e6bad-124">Oculus Rift</span></span>
  * <span data-ttu-id="e6bad-125">Ultraleap ハンド トラッキング</span><span class="sxs-lookup"><span data-stu-id="e6bad-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="e6bad-126">iOS や Android などのモバイル デバイス</span><span class="sxs-lookup"><span data-stu-id="e6bad-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="e6bad-127">MRTK の概要</span><span class="sxs-lookup"><span data-stu-id="e6bad-127">Getting started with MRTK</span></span>

<span data-ttu-id="e6bad-128">Unity での MRTK または Mixed Reality 開発が初めての場合は、必要なツールをインストールした後、HoloLens 2 チュートリアル シリーズに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e6bad-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6bad-129">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="e6bad-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6bad-130">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="e6bad-130">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="e6bad-131">内部的なしくみを確認したい場合は、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e6bad-132">GitHub で MRTK を調べる</span><span class="sxs-lookup"><span data-stu-id="e6bad-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="e6bad-133">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="e6bad-133">Documentation</span></span>

| <span data-ttu-id="e6bad-134">[![リリース ノート](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="e6bad-135">リリース ノート</span><span class="sxs-lookup"><span data-stu-id="e6bad-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="e6bad-136">[![MRTK の概要](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="e6bad-137">MRTK の概要</span><span class="sxs-lookup"><span data-stu-id="e6bad-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="e6bad-138">[![API リファレンス](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="e6bad-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="e6bad-139">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="e6bad-139">API Reference</span></span>](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="e6bad-140">ビルドの状態</span><span class="sxs-lookup"><span data-stu-id="e6bad-140">Build status</span></span>

| <span data-ttu-id="e6bad-141">[Branch]\(ブランチ)</span><span class="sxs-lookup"><span data-stu-id="e6bad-141">Branch</span></span> | <span data-ttu-id="e6bad-142">CI の状態</span><span class="sxs-lookup"><span data-stu-id="e6bad-142">CI Status</span></span> | <span data-ttu-id="e6bad-143">ドキュメントの状態</span><span class="sxs-lookup"><span data-stu-id="e6bad-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="e6bad-144">[![CI の状態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="e6bad-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="e6bad-145">[![ドキュメントの状態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="e6bad-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="e6bad-146">機能領域</span><span class="sxs-lookup"><span data-stu-id="e6bad-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-147">[![入力システム](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[入力システム](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-148">[![ハンド トラッキング (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[ハンド トラッキング <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-148">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-149">[![視線追跡 (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[視線追跡 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-149">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-150">[![プロファイル](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md) **[プロファイル](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-150">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md) **[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-151">[![ハンド トラッキング (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[ハンド トラッキング <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-151">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-152">[![UI コントロール](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[UI コントロール](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-152">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-153">[![ソルバー](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[ソルバー](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-153">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-154">[![マルチシーン マネージャー](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[マルチシーン<br/> マネージャー](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-154">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-155">[![空間認識](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間 <br/> 認識](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-155">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-156">[![診断ツール](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[診断 <br/> ツール](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-156">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-157">[![MRTK 標準シェーダー ビュー](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[MRTK 標準シェーダー ビューの例](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-157">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-158">[![音声認識 & ディクテーション](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[音声認識](features/input/speech.md)<br/> & [ディクテーション](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-158">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-159">[![境界システム](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[境界 <br/>システム](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-159">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-160">[![エディター内シミュレーション](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md) **[エディター内 <br/> シミュレーション](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-160">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md) **[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-161">[![試験的な機能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[試験的な <br/> 機能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-161">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="e6bad-162">UX 構成要素</span><span class="sxs-lookup"><span data-stu-id="e6bad-162">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-163">[![ボタン](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[ボタン](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-163">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="e6bad-164">HoloLens 2 の多関節ハンドを含む各種入力方法がサポートされているボタン コントロール</span><span class="sxs-lookup"><span data-stu-id="e6bad-164">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-165">[![境界コントロール](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[境界コントロール](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-165">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="e6bad-166">3D 空間内のオブジェクトを操作するための標準 UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-166">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-167">[![オブジェクト マニピュレーター](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[オブジェクト マニピュレーター](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-167">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="e6bad-168">片手または両手でオブジェクトを操作するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="e6bad-168">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-169">[![スレート](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[スレート](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-169">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="e6bad-170">多関節ハンド入力によるスクロールがサポートされている 2D スタイルの平面</span><span class="sxs-lookup"><span data-stu-id="e6bad-170">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-171">[![システム キーボード](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[システム キーボード](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-171">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="e6bad-172">Unity でシステム キーボードを使用するサンプル スクリプト</span><span class="sxs-lookup"><span data-stu-id="e6bad-172">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-173">[![対話可能](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[対話可能](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-173">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="e6bad-174">視覚的な状態とテーマのサポートを使用してオブジェクトを対話型にするためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="e6bad-174">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-175">[![ソルバー](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[ソルバー](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-175">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="e6bad-176">追従、本体ロック、ビュー サイズの固定、表面吸着など、さまざまなオブジェクトの配置動作</span><span class="sxs-lookup"><span data-stu-id="e6bad-176">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-177">[![オブジェクト コレクション](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[オブジェクト コレクション](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-177">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="e6bad-178">多数のオブジェクトを 3 次元形状で並べるためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="e6bad-178">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-179">[![ツールヒント](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[ツールヒント](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-179">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="e6bad-180">モーション コントローラーとオブジェクトのラベル付けに使用できる、柔軟なアンカーおよびピボット システムを備えた注釈 UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-180">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-181">[![スライダー](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[スライダー](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-181">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="e6bad-182">直接のハンド トラッキング操作がサポートされている、値調整のためのスライダー UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-182">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-183">[![MRTK 標準シェーダー](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 標準シェーダー](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-183">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="e6bad-184">MRTK の標準シェーダーでは、さまざまな Fluent デザイン要素とパフォーマンスがサポートされています</span><span class="sxs-lookup"><span data-stu-id="e6bad-184">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-185">[![ハンド メニュー](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[ハンド メニュー](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-185">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="e6bad-186">ハンド制約ソルバーを使用した、クイック アクセス用のハンドロック UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-186">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-187">[![アプリ バー](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[アプリ バー](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-187">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="e6bad-188">境界コントロールの手動アクティブ化のための UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-188">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-189">[![ポインター](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[ポインター](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-189">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="e6bad-190">さまざまな種類のポインターについて説明します</span><span class="sxs-lookup"><span data-stu-id="e6bad-190">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-191">[![指先の視覚化](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[指先の視覚化](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-191">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="e6bad-192">直接操作の信頼度を向上させる、指先の視覚的アフォーダンス</span><span class="sxs-lookup"><span data-stu-id="e6bad-192">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-193">[![近くのメニュー](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[近くのメニュー](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-193">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="e6bad-194">近くの対話式操作のための移動メニュー UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-194">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-195">[![空間認識の概要](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間認識ビュー](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-195">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="e6bad-196">ホログラフィック オブジェクトが物理環境と相互作用するようにする</span><span class="sxs-lookup"><span data-stu-id="e6bad-196">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-197">[![音声コマンド](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[音声コマンド](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-197">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="e6bad-198">音声入力を統合するためのスクリプトと例</span><span class="sxs-lookup"><span data-stu-id="e6bad-198">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-199">[![進行状況インジケーター](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[進行状況インジケーター](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-199">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="e6bad-200">データの処理または操作を伝えるための視覚的インジケーター</span><span class="sxs-lookup"><span data-stu-id="e6bad-200">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-201">[![ダイアログ](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[ダイアログ](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-201">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="e6bad-202">ユーザーの確認または同意を求めるための UI</span><span class="sxs-lookup"><span data-stu-id="e6bad-202">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-203">[![ハンド コーチ](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[ハンド コーチ](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-203">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="e6bad-204">ジェスチャが学習されていない場合にユーザーをガイドするのに役立つコンポーネント</span><span class="sxs-lookup"><span data-stu-id="e6bad-204">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-205">[![ハンド物理サービス](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[ハンド物理サービス [試験段階]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-205">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="e6bad-206">ハンド物理サービスによって、剛体の衝突イベントおよび多関節ハンドとの対話が可能になります</span><span class="sxs-lookup"><span data-stu-id="e6bad-206">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-207">[![スクロール可能コレクション](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[スクロール可能コレクション](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-207">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="e6bad-208">3D オブジェクトがネイティブでスクロールされるオブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="e6bad-208">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-209">[![ドック](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[ドック [試験段階]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-209">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="e6bad-210">ドックを使用すると、事前に定義された位置にオブジェクトを出し入れできます</span><span class="sxs-lookup"><span data-stu-id="e6bad-210">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e6bad-211">[![視線追跡: ターゲット選択](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[視線追跡: ターゲット選択](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-211">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="e6bad-212">視線、音声、ハンドの入力を組み合わせて、シーン全体からホログラムをすばやく簡単に選択する</span><span class="sxs-lookup"><span data-stu-id="e6bad-212">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-213">[![視線追跡: ナビゲーション](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[視線追跡: ナビゲーション](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-213">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="e6bad-214">視線に基づいてテキストを自動でスクロールしたり、フォーカスされたコンテンツをなめらかに拡大したりする方法について説明します</span><span class="sxs-lookup"><span data-stu-id="e6bad-214">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e6bad-215">[![視線追跡: ヒート マップ](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[視線追跡: ヒート マップ](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="e6bad-215">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="e6bad-216">アプリ内でユーザーが見ていたもののログ記録、読み込み、視覚化を行う例</span><span class="sxs-lookup"><span data-stu-id="e6bad-216">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="e6bad-217">［ツール］</span><span class="sxs-lookup"><span data-stu-id="e6bad-217">Tools</span></span>

|  <span data-ttu-id="e6bad-218">[![最適化ウィンドウ](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [最適化ウィンドウ](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-218">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="e6bad-219">[![依存関係ウィンドウ](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [依存関係ウィンドウ](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-219">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![ビルド ウィンドウ](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="e6bad-221">ビルド ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="e6bad-221">Build Window</span></span> | <span data-ttu-id="e6bad-222">[![入力記録](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [入力記録](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-222">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="e6bad-223">Mixed Reality プロジェクトの構成を自動化してパフォーマンスを最適化します</span><span class="sxs-lookup"><span data-stu-id="e6bad-223">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="e6bad-224">アセット間の依存関係を分析し、使用されていないアセットを特定します</span><span class="sxs-lookup"><span data-stu-id="e6bad-224">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="e6bad-225">Mixed Reality アプリケーションのエンド ツー エンド ビルド プロセスを構成および実行します</span><span class="sxs-lookup"><span data-stu-id="e6bad-225">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="e6bad-226">エディターで頭の移動とハンド トラッキングのデータを記録および再生します</span><span class="sxs-lookup"><span data-stu-id="e6bad-226">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="e6bad-227">シーンの例</span><span class="sxs-lookup"><span data-stu-id="e6bad-227">Example scenes</span></span>

<span data-ttu-id="e6bad-228">[こちらのシーンの例](features/example-scenes/hand-interaction-examples.md)で、MRTK のさまざまな種類の対話式操作と UI コントロールについて調べます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-228">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="e6bad-229">[![シーンの例 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-229">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="e6bad-230">MRTK Examples Hub</span><span class="sxs-lookup"><span data-stu-id="e6bad-230">MRTK examples hub</span></span>

<span data-ttu-id="e6bad-231">MRTK Examples Hub により、MRTK の各種シーンの例を試すことができます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-231">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="e6bad-232">[MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) で "Mixed Reality Toolkit Examples" パッケージを選択することにより、HoloLens (x86)、HoloLens 2 (ARM)、および Windows Mixed Reality イマーシブ ヘッドセット (x64) 向けの事前構築済みアプリ パッケージをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-232">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="e6bad-233">[Windows デバイス ポータルを使って HoloLens (第 1 世代) にアプリをインストールする](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)ようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-233">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="e6bad-234">HoloLens 2 では、[Microsoft Store アプリから MRTK Examples Hub](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4) をダウンロードしてインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-234">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="e6bad-235">MRTK のシーン システムとシーン切り替えサービスを使用してマルチシーン ハブを作成する方法の詳細については、[Examples Hub の README ページ](features/example-scenes/example-hub.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-235">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="e6bad-236">[![シーンの例ハブ](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="e6bad-236">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="e6bad-237">MRTK を使用して作成されたサンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="e6bad-237">Sample apps made with MRTK</span></span>

| <span data-ttu-id="e6bad-238">[![要素の定期的なテーブル](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="e6bad-238">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="e6bad-239">[![銀河エクスプローラー](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="e6bad-239">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="e6bad-240">[![Surfaces サンプル アプリ](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="e6bad-240">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="e6bad-241">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) は、MRTK の入力システムと構成要素を使用して HoloLens およびイマーシブ ヘッドセット用のアプリ エクスペリエンスを作成する方法を示す、オープンソースのサンプル アプリです。</span><span class="sxs-lookup"><span data-stu-id="e6bad-241">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="e6bad-242">移植のストーリーをご覧ください: 「[MRTK v2 を使用して Periodic Table of the Elements アプリを HoloLens 2 に移植する](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)」</span><span class="sxs-lookup"><span data-stu-id="e6bad-242">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="e6bad-243">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) は、元は 2016 年 3 月に HoloLens 'Share Your Idea' キャンペーンの一環として開発された、オープンソースのサンプル アプリです。</span><span class="sxs-lookup"><span data-stu-id="e6bad-243">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="e6bad-244">Galaxy Explorer は、MRTK v2 を使用して、HoloLens 2 の新機能によって更新されました。</span><span class="sxs-lookup"><span data-stu-id="e6bad-244">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="e6bad-245">次のストーリーをご覧ください: 「[ HoloLens 2 用 Galaxy Explorer の作成](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)」</span><span class="sxs-lookup"><span data-stu-id="e6bad-245">Read the story: [The Making of Galaxy Explorer for HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="e6bad-246">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) は HoloLens 2 用のオープンソースのサンプル アプリです。視覚、音声、完全な多関節ハンド トラッキングを使用して、触覚が作られるしくみを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-246">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="e6bad-247">設計と開発の詳しいストーリーについては、Microsoft MR Dev Days のセッション「[Surfaces アプリを使った学習](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-247">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="e6bad-248">Mixed Reality Dev Days 2020 のセッションのビデオ</span><span class="sxs-lookup"><span data-stu-id="e6bad-248">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="e6bad-249">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="e6bad-249">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="e6bad-250">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="e6bad-250">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="e6bad-251">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="e6bad-251">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="e6bad-252">シンプルな MRTK アプリを、最初から最後まで作成する方法についてのチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="e6bad-252">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="e6bad-253">対話式操作の概念と MRTK のマルチプラットフォーム機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-253">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="e6bad-254">美しい Mixed Reality エクスペリエンスの構築に役立つ、MRTK の UX 構成要素について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-254">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="e6bad-255">パフォーマンス ツール (MRTK および外部ツールの両方) を紹介し、MRTK 標準シェーダーの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-255">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="e6bad-256">その他のセッション ビデオについては、[Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-256">See [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="e6bad-257">コミュニティに参加する</span><span class="sxs-lookup"><span data-stu-id="e6bad-257">Engage with the community</span></span>

* <span data-ttu-id="e6bad-258">[Slack](https://holodevelopers.slack.com/) で MRTK に関する会話に参加します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-258">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="e6bad-259">[自動招待センダー](https://holodevelopersslack.azurewebsites.net/)を使用して Slack コミュニティに参加することができます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-259">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="e6bad-260">[Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) で、**MRTK** タグを使用して MRTK の使用に関する質問をします。</span><span class="sxs-lookup"><span data-stu-id="e6bad-260">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="e6bad-261">MRTK コード内に破損を見つけた場合は、[既知のイシュー](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)を検索するか、[新しいイシュー](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)を報告します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-261">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="e6bad-262">MRTK への投稿に関する質問については、slack の [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) チャンネルにアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-262">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="e6bad-263">このプロジェクトは、「[Microsoft のオープン ソースの倫理規定](https://opensource.microsoft.com/codeofconduct/)」を採用しています。</span><span class="sxs-lookup"><span data-stu-id="e6bad-263">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="e6bad-264">詳細については、[倫理規定の FAQ](https://opensource.microsoft.com/codeofconduct/faq/) のページを参照してください。また、追加の質問やコメントがある場合は [opencode@microsoft.com](mailto:opencode@microsoft.com) にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-264">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="e6bad-265">Mixed Reality デベロッパー センターの便利なリソース</span><span class="sxs-lookup"><span data-stu-id="e6bad-265">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="e6bad-266">![見つける](features/images/mrdevcenter/icon-discover.png) [見つける](https://docs.microsoft.com/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="e6bad-266">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](https://docs.microsoft.com/windows/mixed-reality/)</span></span>| <span data-ttu-id="e6bad-267">![設計](features/images/mrdevcenter/icon-design.png) [設計](https://docs.microsoft.com/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="e6bad-267">![Design](features/images/mrdevcenter/icon-design.png) [Design](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>| <span data-ttu-id="e6bad-268">![開発](features/images/mrdevcenter/icon-develop.png) [開発](https://docs.microsoft.com/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="e6bad-268">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](https://docs.microsoft.com/windows/mixed-reality/development)</span></span>| <span data-ttu-id="e6bad-269">![配布)](features/images/mrdevcenter/icon-distribute.png) [配布](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="e6bad-269">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="e6bad-270">HoloLens とイマーシブ ヘッドセット (VR) 向けの Mixed Reality エクスペリエンスを構築する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-270">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="e6bad-271">デザイン ガイドを入手します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-271">Get design guides.</span></span> <span data-ttu-id="e6bad-272">ユーザー インターフェイスを構築します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-272">Build user interface.</span></span> <span data-ttu-id="e6bad-273">対話式操作と入力について学習します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-273">Learn interactions and input.</span></span>     | <span data-ttu-id="e6bad-274">開発ガイドを入手します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-274">Get development guides.</span></span> <span data-ttu-id="e6bad-275">テクノロジを学習します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-275">Learn the technology.</span></span> <span data-ttu-id="e6bad-276">科学を理解します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-276">Understand the science.</span></span>       | <span data-ttu-id="e6bad-277">他のユーザー用にアプリを準備し、3D ランチャーの作成を検討します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-277">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="e6bad-278">Azure の便利なリソース</span><span class="sxs-lookup"><span data-stu-id="e6bad-278">Useful resources on Azure</span></span>

| <span data-ttu-id="e6bad-279">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="e6bad-279">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="e6bad-280">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e6bad-280">Spatial Anchors</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)| <span data-ttu-id="e6bad-281">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="e6bad-281">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="e6bad-282">![視覚サービス](features/images/mrdevcenter/icon-azurevisionservices.png) [視覚サービス](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="e6bad-282">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="e6bad-283">Spatial Anchors は、時間が経過しても複数のデバイス間で位置が維持されるオブジェクトを使用した Mixed Reality エクスペリエンスを作成できる、クロスプラットフォーム サービスです。</span><span class="sxs-lookup"><span data-stu-id="e6bad-283">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="e6bad-284">音声テキスト変換、話者認識、アプリケーションへの音声変換など Azure を利用した音声認識機能を検出、統合します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-284">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="e6bad-285">コンピューター ビジョン、顔検出、感情認識、Video Indexer などのビジョン サービスを使用して画像またはビデオ コンテンツを特定、分析します。</span><span class="sxs-lookup"><span data-stu-id="e6bad-285">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="e6bad-286">貢献する方法</span><span class="sxs-lookup"><span data-stu-id="e6bad-286">How to contribute</span></span>

<span data-ttu-id="e6bad-287">MRTK に投稿する方法については、「[投稿](contributing/contributing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-287">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="e6bad-288">ヘルプの表示</span><span class="sxs-lookup"><span data-stu-id="e6bad-288">Getting help</span></span>

<span data-ttu-id="e6bad-289">MRTK に起因する問題が発生した場合、または何かを行う方法について質問がある場合は、いくつかのリソースが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-289">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="e6bad-290">バグ レポートを行う場合は、GitHub リポジトリで[イシューを報告](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)してください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-290">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="e6bad-291">ご質問がある場合は、[StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) か Slack の [mixed-reality-toolkit チャンネル](https://holodevelopers.slack.com/messages/C2H4HT858)のいずれかをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="e6bad-291">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="e6bad-292">[自動招待センダー](https://holodevelopersslack.azurewebsites.net/)を使用して Slack コミュニティに参加することができます。</span><span class="sxs-lookup"><span data-stu-id="e6bad-292">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>
