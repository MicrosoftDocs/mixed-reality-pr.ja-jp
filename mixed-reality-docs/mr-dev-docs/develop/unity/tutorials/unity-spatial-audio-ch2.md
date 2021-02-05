---
title: 空間オーディオチュートリアル-2. ボタンの対話式操作サウンドの立体化
description: ボタンをプロジェクトに追加し、ボタンの相互作用サウンドを spatialize します。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、prefabs、volume curve
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590764"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="72e26-105">2.ボタンの対話式操作サウンドの立体化</span><span class="sxs-lookup"><span data-stu-id="72e26-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="72e26-106">概要</span><span class="sxs-lookup"><span data-stu-id="72e26-106">Overview</span></span>

<span data-ttu-id="72e26-107">このチュートリアルでは、ボタンの相互作用音を spatialize する方法と、オーディオクリップを使用して spatialized ボタンの対話をテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72e26-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="72e26-108">目標</span><span class="sxs-lookup"><span data-stu-id="72e26-108">Objectives</span></span>

* <span data-ttu-id="72e26-109">ボタンのクリック音を追加して Spatialize</span><span class="sxs-lookup"><span data-stu-id="72e26-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="72e26-110">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="72e26-110">Add a button</span></span>

<span data-ttu-id="72e26-111">Prefab ボタンを追加するには、[ **プロジェクト** ] ウィンドウで [ **パッケージ** ] を選択し、検索バーに「PressableButtonHoloLens2」と入力します。</span><span class="sxs-lookup"><span data-stu-id="72e26-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![アセット内のボタンの事前 fab](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="72e26-113">ボタン prefab は、青いアイコンで表されるエントリです。</span><span class="sxs-lookup"><span data-stu-id="72e26-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="72e26-114">**PressableButtonHoloLens2** prefab をクリックして階層にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="72e26-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="72e26-115">**PressableButtonHoloLens2** オブジェクトを選択した状態で、[インスペクター] ウィンドウで、**変換** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="72e26-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="72e26-116">**位置**: X = 0、Y =-0.4、Z = 2</span><span class="sxs-lookup"><span data-stu-id="72e26-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="72e26-117">**回転**:X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="72e26-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="72e26-118">**スケール**:X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="72e26-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![ボタンの変換](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="72e26-120">シーン内のオブジェクトに焦点を当てるには、 **PressableButtonHoloLens2** オブジェクトをダブルクリックして、もう一度少しズームします。</span><span class="sxs-lookup"><span data-stu-id="72e26-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="72e26-121">Spatialize button のフィードバック</span><span class="sxs-lookup"><span data-stu-id="72e26-121">Spatialize button feedback</span></span>

<span data-ttu-id="72e26-122">この手順では、ボタンの音声フィードバックを spatialize します。</span><span class="sxs-lookup"><span data-stu-id="72e26-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="72e26-123">関連する設計の提案については、「 [空間サウンドの設計](../../../design/spatial-sound-design.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72e26-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="72e26-124">オーディオ **ミキサー** ウィンドウでは、**オーディオソース** コンポーネントからのオーディオ再生用に、**ミキサーグループ** と呼ばれる宛先を定義します。</span><span class="sxs-lookup"><span data-stu-id="72e26-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="72e26-125">[**オーディオミキサー** ] ウィンドウを開くには、Unity メニューで [ **window**  >  **audio**  >  **audio mixer**: ![ open audio ミキサ window] を選択します。](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="72e26-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="72e26-126">ミキサーの **横にある**[+] をクリックし、[_空間オーディオミキサー_] などの適切な名前をミキサーに入力して、**ミキサー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="72e26-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="72e26-127">新しいミキサーには、 **Master** という名前の既定の **グループ** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="72e26-127">The new mixer will include a default **Group** called **Master**.</span></span>

![最初のミキサーがあるミキサーパネル](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="72e26-129">5番目の章でリバーブが有効になるまで [: リバーブを使用して空間オーディオに距離を追加する](unity-spatial-audio-ch5.md)まで、ミキサーのボリュームメーターには、Microsoft Spatializer で再生されるサウンドのアクティビティが表示されません。</span><span class="sxs-lookup"><span data-stu-id="72e26-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="72e26-130">[階層] ウィンドウで **PressableButtonHoloLens2** を選択し、[インスペクター] ウィンドウで **オーディオソース** コンポーネントを見つけて、次のようにオーディオソースコンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="72e26-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="72e26-131">[ **出力** ] プロパティで、セレクターをクリックし、作成した **ミキサー** を選択します。</span><span class="sxs-lookup"><span data-stu-id="72e26-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="72e26-132">**Spatialize** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="72e26-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="72e26-133">[ **空間 Blend** ] スライダーを 3d (1) に移動します。</span><span class="sxs-lookup"><span data-stu-id="72e26-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![ボタンオーディオソース](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="72e26-135">**Spatialize** チェックボックスをオフにして **空間ブレンド** を 1 (3d) に移動すると、Unity では、 **Microsoft spatializer** と hrtfs ではなく、そのパン spatializer が使用されます。</span><span class="sxs-lookup"><span data-stu-id="72e26-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="72e26-136">ボリューム曲線を調整する</span><span class="sxs-lookup"><span data-stu-id="72e26-136">Adjust the Volume curve</span></span>

<span data-ttu-id="72e26-137">既定では、Unity はリスナーから遠く離れた spatialized サウンドを減衰します。</span><span class="sxs-lookup"><span data-stu-id="72e26-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="72e26-138">この減衰が相互作用フィードバックのサウンドに適用されると、インターフェイスの使用が困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72e26-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="72e26-139">この減衰を無効にするには、**オーディオソース** コンポーネントの **ボリューム** 曲線を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72e26-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="72e26-140">[階層] ウィンドウで **PressableButtonHoloLens2** を選択し、[インスペクター] ウィンドウで [**オーディオソース** 3d のサウンド設定] に移動して、次のように  >  構成します。</span><span class="sxs-lookup"><span data-stu-id="72e26-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="72e26-141">ボリュームの **ロール** アウトプロパティを線形ロールオフに設定します</span><span class="sxs-lookup"><span data-stu-id="72e26-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="72e26-142">Y 軸の "0" から "1" までの **ボリューム** 曲線 (赤の曲線) のエンドポイントをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="72e26-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="72e26-143">**ボリューム** 曲線の形状をフラットに調整するには、[白い曲線図形] コントロールを [X 軸] に平行にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="72e26-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Button 3D サウンド設定](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="72e26-145">Spatialize オーディオのテスト</span><span class="sxs-lookup"><span data-stu-id="72e26-145">Testing the spatialize audio</span></span>

<span data-ttu-id="72e26-146">Unity エディターで spatialize オーディオをテストするには、 **PressableButtonHoloLens2** オブジェクトで [**ループ**] オプションがオンになっているオーディオ **ソース** コンポーネントにオーディオクリップを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72e26-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="72e26-147">Play モードでは、 **PressableButtonHoloLens2** オブジェクトを左から右に移動し、ワークステーションで空間オーディオが有効になっているか、使用されていない状態で比較します。</span><span class="sxs-lookup"><span data-stu-id="72e26-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="72e26-148">次の方法で、テスト用のオーディオソース設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="72e26-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="72e26-149">0-1 (2D spatialized と 3D spatialized sound) 間の **空間ブレンド** プロパティの移動</span><span class="sxs-lookup"><span data-stu-id="72e26-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="72e26-150">**Spatialize** プロパティをチェックしてオフにする</span><span class="sxs-lookup"><span data-stu-id="72e26-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="72e26-151">HoloLens 2 でアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="72e26-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="72e26-152">アプリでは、ボタンをクリックすると、spatialized ボタンの相互作用音が聞こえます。</span><span class="sxs-lookup"><span data-stu-id="72e26-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="72e26-153">HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72e26-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="72e26-154">結論</span><span class="sxs-lookup"><span data-stu-id="72e26-154">Congratulations</span></span>

<span data-ttu-id="72e26-155">このチュートリアルでは、ボタンの相互作用音を spatialize、オーディオクリップを使用して spatialized ボタンの対話をテストする方法について学びました。</span><span class="sxs-lookup"><span data-stu-id="72e26-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="72e26-156">次のチュートリアルでは、ビデオソースからオーディオを spatialize する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72e26-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72e26-157">次のチュートリアル: ビデオからの Spatializing オーディオ</span><span class="sxs-lookup"><span data-stu-id="72e26-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
