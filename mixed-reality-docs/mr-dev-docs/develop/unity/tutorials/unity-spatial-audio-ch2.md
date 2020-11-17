---
title: 空間オーディオチュートリアル-2. ボタンの対話式操作サウンドの立体化
description: ボタンをプロジェクトに追加し、ボタンの相互作用サウンドを spatialize します。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、prefabs、volume curve
ms.openlocfilehash: eb550c3127e13926d73428b337abfd7cf9872eb7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678191"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="4fb85-105">ボタンの対話式操作サウンドの立体化</span><span class="sxs-lookup"><span data-stu-id="4fb85-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="4fb85-106">目標</span><span class="sxs-lookup"><span data-stu-id="4fb85-106">Objectives</span></span>
<span data-ttu-id="4fb85-107">HoloLens 2 チュートリアルの空間オーディオモジュールの2番目の章では、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="4fb85-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="4fb85-108">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="4fb85-108">Add a button</span></span>
* <span data-ttu-id="4fb85-109">ボタンのクリック音を Spatialize</span><span class="sxs-lookup"><span data-stu-id="4fb85-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="4fb85-110">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="4fb85-110">Add a button</span></span>
<span data-ttu-id="4fb85-111">[ **プロジェクト** ] ウィンドウで、[ **資産** ] を選択し、検索バーに「PressableButtonHoloLens2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![アセット内のボタンの事前 fab](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="4fb85-113">ボタン prefab は、白いアイコンではなく、青いアイコンで表されるエントリです。</span><span class="sxs-lookup"><span data-stu-id="4fb85-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="4fb85-114">**PressableButtonHoloLens2** という名前の prefab を [**階層**] ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="4fb85-115">新しいボタンの [ **インスペクター** ] ウィンドウで、[ **Position** ] プロパティを (0,-0.4, 2) に設定して、アプリケーションの起動時にユーザーの前に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="4fb85-116">ボタンの **変換** コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-116">The **Transform** component of the button will look like this:</span></span>

![ボタンの変換](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="4fb85-118">Spatialize button のフィードバック</span><span class="sxs-lookup"><span data-stu-id="4fb85-118">Spatialize button feedback</span></span>
<span data-ttu-id="4fb85-119">この手順では、ボタンの音声フィードバックを spatialize します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="4fb85-120">関連する設計の提案については、「 [空間サウンドの設計](../../../design/spatial-sound-design.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb85-120">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="4fb85-121">オーディオ **ミキサー** ウィンドウでは、**オーディオソース** コンポーネントからのオーディオ再生用に **ミキサーグループ** と呼ばれる宛先を定義します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="4fb85-122">メニューバーの [audio **> Audio ミキサー] >** を使用して、[**オーディオミキサー** ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4fb85-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="4fb85-123">**ミキサー** の横にある [+] をクリックして、ミキサーを作成 **します。**</span><span class="sxs-lookup"><span data-stu-id="4fb85-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="4fb85-124">新しいミキサーには、 **Master** という名前の既定の **グループ** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4fb85-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="4fb85-125">**ミキサー** ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-125">Your **Mixer** pane will now look like this:</span></span>

![最初のミキサーがあるミキサーパネル](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="4fb85-127">[5 章](unity-spatial-audio-ch5.md)のリバーブが有効になるまで、ミキサーのボリュームメーターには、Microsoft Spatializer で再生されるサウンドのアクティビティが表示されません。</span><span class="sxs-lookup"><span data-stu-id="4fb85-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="4fb85-128">[**階層**] ペインで **PressableButtonHoloLens2** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="4fb85-129">[ **インスペクター** ] ウィンドウで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="4fb85-130">**オーディオソース** コンポーネントを検索する</span><span class="sxs-lookup"><span data-stu-id="4fb85-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="4fb85-131">[ **出力** ] プロパティで、セレクターをクリックし、ミキサーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="4fb85-132">**Spatialize** チェックボックスをオンにする</span><span class="sxs-lookup"><span data-stu-id="4fb85-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="4fb85-133">[ **空間 Blend** ] スライダーを 3d (1) に移動します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="4fb85-134">2019より前のバージョンの Unity では、[Spatialize] チェックボックスは、**オーディオソース** の [**インスペクター** ] ウィンドウの下部にあります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="4fb85-135">これらの変更が完了すると、 **PressableButtonHoloLens2** の **オーディオソース** コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![ボタンオーディオソース](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="4fb85-137">**Spatialize** チェックボックスをオフにして **空間ブレンド** を 1 (3d) に移動すると、Unity では、 **Microsoft spatializer** と hrtfs ではなく、そのパン spatializer が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4fb85-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="4fb85-138">ボリューム曲線を調整する</span><span class="sxs-lookup"><span data-stu-id="4fb85-138">Adjust the Volume curve</span></span>
<span data-ttu-id="4fb85-139">既定では、Unity はリスナーから遠く離れた spatialized サウンドを減衰します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="4fb85-140">この減衰が相互作用フィードバックのサウンドに適用されると、インターフェイスの使用が困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="4fb85-141">この減衰を無効にするには、 **ボリューム** 曲線を調整します。</span><span class="sxs-lookup"><span data-stu-id="4fb85-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="4fb85-142">**PressableButtonHoloLens2** の [**インスペクター** ] ウィンドウの [**オーディオソース**] コンポーネントには、[ **3d サウンド設定**] というセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="4fb85-143">そのセクション内:</span><span class="sxs-lookup"><span data-stu-id="4fb85-143">In that section:</span></span>
1. <span data-ttu-id="4fb85-144">ボリュームの **ロールロール** のプロパティを線形に設定する</span><span class="sxs-lookup"><span data-stu-id="4fb85-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="4fb85-145">Y 軸の "0" から "1" までの **ボリューム** 曲線 (赤の曲線) のエンドポイントをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="4fb85-146">**ボリューム** 曲線の形状をフラットに調整するには、[白い曲線図形] コントロールを [X 軸] に平行にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="4fb85-147">これらの変更が完了すると、 **PressableButtonHoloLens2** の **オーディオソース** プロパティの **3d サウンド設定** セクションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Button 3D サウンド設定](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="4fb85-149">Spatialize オーディオのテスト</span><span class="sxs-lookup"><span data-stu-id="4fb85-149">Testing the spatialize audio</span></span>

<span data-ttu-id="4fb85-150">新しい spatialized ボタンの相互作用音を自由に試してください。</span><span class="sxs-lookup"><span data-stu-id="4fb85-150">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="4fb85-151">Unity エディターでゲームモードに入る (理想的にはシーンのループオーディオサンプルを使用する)</span><span class="sxs-lookup"><span data-stu-id="4fb85-151">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="4fb85-152">オーディオソースを持つオブジェクトを左から右へ移動し、空間オーディオを有効にした場合と比較した場合の比較を行います。</span><span class="sxs-lookup"><span data-stu-id="4fb85-152">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="4fb85-153">テストのオーディオソース設定を変更するには、次の方法があります。</span><span class="sxs-lookup"><span data-stu-id="4fb85-153">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="4fb85-154">0-1 (2D spatialized と 3D spatialized sound) 間の空間ブレンドプロパティの移動</span><span class="sxs-lookup"><span data-stu-id="4fb85-154">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="4fb85-155">Spatialize プロパティをチェックしてオフにする</span><span class="sxs-lookup"><span data-stu-id="4fb85-155">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="4fb85-156">次のステップ</span><span class="sxs-lookup"><span data-stu-id="4fb85-156">Next steps</span></span>

<span data-ttu-id="4fb85-157">HoloLens 2 または Unity エディターでアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="4fb85-157">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="4fb85-158">アプリでは、ボタンをタッチして、spatialized ボタンの相互作用音を聞くことができます。</span><span class="sxs-lookup"><span data-stu-id="4fb85-158">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="4fb85-159">Unity エディターでテストする場合は、スペースバーを押し、スクロールホイールを使用してスクロールし、ハンドシミュレーションをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="4fb85-159">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="4fb85-160">詳細については、 [Mrtk のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb85-160">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fb85-161">章3</span><span class="sxs-lookup"><span data-stu-id="4fb85-161">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

