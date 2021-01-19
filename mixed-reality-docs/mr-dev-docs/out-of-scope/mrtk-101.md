---
title: MRTK 101 - 一般的な空間操作の使用
description: HoloLens 2、HoloLens、Windows Mixed Reality、Open VR の基本的な操作に Mixed Reality Toolkit Unity を使用する方法。
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 設計, サンプル アプリ, コントロール, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98248148"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="d72f5-104">MRTK 101: 一般的な空間操作に Mixed Reality Toolkit Unity を使用する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="d72f5-106">MRTK を使用して、Mixed Reality で最も広く使用されている一般的な対話式操作パターンを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="d72f5-107">Unity エディターで入力の対話式操作をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="d72f5-108">オブジェクトをつかんで動かす方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-108">How to grab and move an object?</span></span>
- <span data-ttu-id="d72f5-109">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-109">How to resize an object?</span></span>
- <span data-ttu-id="d72f5-110">正確にオブジェクトを動かしたり回転させたりする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="d72f5-111">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="d72f5-112">視覚的なフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-112">How to add visual feedback?</span></span>
- <span data-ttu-id="d72f5-113">音声によるフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-113">How to add audio feedback?</span></span>
- <span data-ttu-id="d72f5-114">HoloLens 2 のスタイル ボタン プレハブを使用する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="d72f5-115">オブジェクトが自分の後をついてくるようにする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-115">How to make an object follow you?</span></span>
- <span data-ttu-id="d72f5-116">オブジェクトが自分の方を向くようにする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="d72f5-117">この記事は、[MRTK v2.5.1 リリース](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)での変更を反映するように更新されています</span><span class="sxs-lookup"><span data-stu-id="d72f5-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="d72f5-118">このページの内容はすべて、Unity エディターで MRTK の入力シミュレーションを使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="d72f5-119">まだ行っていない場合は、[MRTK のインストール ガイド (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) に従って、MRTK の最新バージョンをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="d72f5-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="d72f5-120">Unity エディターで入力の対話式操作をシミュレートする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="d72f5-121">MRTK では、エディター内入力シミュレーションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d72f5-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="d72f5-122">Unity の [Play]\(再生\) ボタンをクリックしてシーンを実行し、次のキーを使用して入力をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="d72f5-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="d72f5-123">カメラを動かすには、W、A、S、D のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="d72f5-124">周囲を見回すには、マウスの右ボタンを押したまま、マウスを動かします。</span><span class="sxs-lookup"><span data-stu-id="d72f5-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="d72f5-125">Space キー (右手) または左 Shift キー (左手) を押して、シミュレートされた手を表示します</span><span class="sxs-lookup"><span data-stu-id="d72f5-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="d72f5-126">T キーまたは Y キーを押して、シミュレートされた手のビューを保持します</span><span class="sxs-lookup"><span data-stu-id="d72f5-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="d72f5-127">シミュレートされた手を回転させるには、Q または E (横方向)、R または F (縦方向) の各キーを押します</span><span class="sxs-lookup"><span data-stu-id="d72f5-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="d72f5-128">入力シミュレーションの詳細については、[MRTK のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d72f5-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="d72f5-129">オブジェクトをつかんで動かす方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-129">How to grab and move an object?</span></span>

<span data-ttu-id="d72f5-130">**ObjectManipulator.cs** および **NearInteractionGrabbable.cs** スクリプトをアタッチして、オブジェクトを取得可能にします。</span><span class="sxs-lookup"><span data-stu-id="d72f5-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="d72f5-131">ObjectManipulator では、近距離と遠距離の両方の対話式操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d72f5-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="d72f5-132">オブジェクトをつかんで動かすには、HoloLens 2 の多関節ハンド トラッキング入力 (近く)、ハンド レイ (遠く)、モーション コントローラーのビーム (遠く)、HoloLens の視線カーソルとエアタップ (遠く) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="d72f5-133">オブジェクトのサイズを変更する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-133">How to resize an object?</span></span>
<span data-ttu-id="d72f5-134">**ObjectManipulator.cs** では、両手のスケーリングと回転がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d72f5-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="d72f5-135">このスクリプトは、HoloLens 2 の多関節ハンド入力、HoloLens 1 の視線入力とジェスチャ入力、Windows Mixed Reality のイマーシブ ヘッドセットのモーション コントローラー入力など、さまざまな入力の種類で機能します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="d72f5-136">Learn more about Object の詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="d72f5-137">正確にオブジェクトを動かしたり回転させたりする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="d72f5-138">オブジェクトをスケーリングしたり回転させたりするためのインターフェイスである境界ボックスを使用するには、**BoundsControl.cs** をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="d72f5-139">既定では、HoloLens 1 スタイルの青いハンドルとワイヤが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="d72f5-140">HoloLens 2 スタイルの近接度に基づくアニメーション ハンドルを使用するには、プレハブとマテリアルを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d72f5-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="d72f5-141">境界コントロールの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="d72f5-142">オブジェクトを入力イベントに応答させる方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="d72f5-143">**PointerHandler.cs** をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="d72f5-144">インスペクターでは、OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() のイベントを使用できます。これらのイベントをスクリプトで使用するには、**IMixedRealityPointerHandler** を実装します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="d72f5-145">入力システムの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="d72f5-146">視覚的なフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-146">How to add visual feedback?</span></span>
<span data-ttu-id="d72f5-147">**Interactable.cs** をオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="d72f5-148">インスペクターで、ターゲット オブジェクトを追加し、新しいテーマを作成します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="d72f5-149">Interactable のテーマ プロファイルを使用すると、利用可能なすべての入力対話式操作状態に視覚的なフィードバックを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="d72f5-150">Interactable には、対話式操作状態ごとにシェーダーのプロパティを制御できるようにするシェーダー テーマを含め、さまざまな種類のテーマが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d72f5-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="d72f5-151">Interactable の詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="d72f5-152">視覚的なフィードバックのもう 1 つの重要な構成要素は、**MRTK 標準シェーダー** です。</span><span class="sxs-lookup"><span data-stu-id="d72f5-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="d72f5-153">MRTK 標準シェーダーを使用すると、ホバー ライトや近接ライトなどの視覚的なフィードバック効果を簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="d72f5-154">MRTK 標準シェーダーで実行される計算は、Unity 標準シェーダーより少ないため、効率の良いエクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="d72f5-155">新しいマテリアルを作成し、[Shader]\(シェーダー\) で [Mixed Reality Toolkit] > [Standard]\(標準\) の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="d72f5-156">あるいは、MRTK 標準シェーダーを使用する既存のマテリアルのいずれかを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="d72f5-157">MRTK 標準シェーダーの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="d72f5-158">音声によるフィードバックを追加する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-158">How to add audio feedback?</span></span>
<span data-ttu-id="d72f5-159">**AudioSource** をオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="d72f5-160">次に、入力イベントを公開するスクリプト (例: Interactable.cs や PointerHandler.cs) で、AudioSource のあるオブジェクトをイベントに割り当て、**AudioSource.PlayOneShot()** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d72f5-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="d72f5-161">自分のオーディオ クリップを使用することも、MRTK のオーディオ アセットのいずれかを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="d72f5-162">HoloLens 2 のスタイル ボタン プレハブを使用する方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="d72f5-163">MRTK には、さまざまな種類の HoloLens 2 のシェル (OS) スタイルのボタンが用意されています。たとえば、近接ライト、圧縮ボックス、ボタン サーフェスの波紋効果など、ユーザーの信頼度を高める視覚的なフィードバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="d72f5-164">**HoloLens 2 スタイル押しボタン プレハブ** をシーンにドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="d72f5-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="d72f5-165">プレハブには、上記で導入された Interactable.cs が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="d72f5-166">Interactable で OnClick() などの公開されたイベントを使用してアクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="d72f5-167">Button プレハブの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="d72f5-168">オブジェクトが自分の後をついてくるようにする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-168">How to make an object follow you?</span></span>
<span data-ttu-id="d72f5-169">**RadialView.cs** または **Follow.cs** スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="d72f5-170">これは、Solver スクリプト シリーズの一部です。これを使用すると、3D 空間に配置されているさまざまな種類のオブジェクトを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="d72f5-171">**SolverHandler.cs** は自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="d72f5-172">次に示すのは、HoloLens シェルの [スタート] メニューと同様に、"lazy follow" Tag-along 動作を実現する RadialView 構成の例です。</span><span class="sxs-lookup"><span data-stu-id="d72f5-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="d72f5-173">最小/最大の距離と最小/最大の表示角度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="d72f5-174">次の例は、0.4 m と 0.8 m の範囲で 15°以内のオブジェクトの配置を示しています。</span><span class="sxs-lookup"><span data-stu-id="d72f5-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="d72f5-175">Lerp 時間の値を調整して、位置指定の更新を速くしたり遅くしたりします。</span><span class="sxs-lookup"><span data-stu-id="d72f5-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="d72f5-176">ソルバーの詳細については、MRTK のドキュメントを参照してください</span><span class="sxs-lookup"><span data-stu-id="d72f5-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="d72f5-177">オブジェクトが自分の方を向くようにする方法</span><span class="sxs-lookup"><span data-stu-id="d72f5-177">How to make an object face you?</span></span>
<span data-ttu-id="d72f5-178">**Billboard.cs** スクリプトをオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="d72f5-179">自分の位置にかかわらず、常に自分の方を向くようになります。</span><span class="sxs-lookup"><span data-stu-id="d72f5-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="d72f5-180">ピボット軸オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d72f5-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="d72f5-181">Mixed Reality の素晴らしいエクスペリエンスを作成する準備はできましたか。</span><span class="sxs-lookup"><span data-stu-id="d72f5-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="d72f5-182">MRTK と Mixed Reality の詳細については、以下のページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d72f5-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d72f5-183">筆者について</span><span class="sxs-lookup"><span data-stu-id="d72f5-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d72f5-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d72f5-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d72f5-185">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d72f5-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d72f5-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="d72f5-186">See also</span></span>
* [<span data-ttu-id="d72f5-187">MRTK インストール ガイド (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d72f5-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="d72f5-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="d72f5-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="d72f5-189">MRTK ドキュメント ポータル (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d72f5-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d72f5-190">HoloToolkit から MRTK への移植ガイドライン</span><span class="sxs-lookup"><span data-stu-id="d72f5-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
