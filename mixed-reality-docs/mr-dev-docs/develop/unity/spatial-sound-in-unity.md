---
title: Unity の立体音響
description: Unity シーン内の特定の3D ポイントから空間サウンドを再生します。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit、spatializer、リバーブ
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010143"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="2c738-104">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="2c738-104">Spatial sound in Unity</span></span>

<span data-ttu-id="2c738-105">このページでは、Unity の空間サウンドのリソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="2c738-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="2c738-106">Spatializer オプション</span><span class="sxs-lookup"><span data-stu-id="2c738-106">Spatializer options</span></span>
<span data-ttu-id="2c738-107">Mixed reality アプリケーションの Spatializer オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c738-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="2c738-108">Unity では、 *Windows Mixed Reality* のオプションパッケージの一部として *MS HRTF Spatializer* を提供しています。</span><span class="sxs-lookup"><span data-stu-id="2c738-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="2c738-109">高コストの ' 単一ソース ' アーキテクチャで CPU 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c738-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="2c738-110">元の HoloLens アプリケーションとの下位互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c738-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="2c738-111">Microsoft *Spatializer* は、 [microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="2c738-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="2c738-112">低コストの ' マルチソース ' アーキテクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c738-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="2c738-113">HoloLens 2 のハードウェアアクセラレータにオフロードされます。</span><span class="sxs-lookup"><span data-stu-id="2c738-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="2c738-114">新しいアプリケーションの場合は、 *Microsoft Spatializer* をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c738-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="2c738-115">Spatialization を有効にする</span><span class="sxs-lookup"><span data-stu-id="2c738-115">Enable spatialization</span></span>

<span data-ttu-id="2c738-116">[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して _SpatialAudio_ をインストールし、プロジェクトのオーディオ設定で **microsoft Spatializer** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c738-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="2c738-117">次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="2c738-117">Then:</span></span>
* <span data-ttu-id="2c738-118">階層内のオブジェクトに **オーディオソース** をアタッチする</span><span class="sxs-lookup"><span data-stu-id="2c738-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="2c738-119">[ **Enable spatialization** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2c738-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="2c738-120">**空間ブレンド** スライダーを ' 1 ' に移動します</span><span class="sxs-lookup"><span data-stu-id="2c738-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="2c738-121">開発者ワークステーションで空間オーディオが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c738-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="2c738-122">タスクバーのボリュームアイコンを右クリックし、[空間サウンド] が [オフ] 以外に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c738-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="2c738-123">**Windows Sonic For ヘッドホン** を選択すると、HoloLens 2 で聞く内容を最適に表示できます。</span><span class="sxs-lookup"><span data-stu-id="2c738-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="2c738-124">Unity で、その依存関係の1つが見つからないために SpatialAudio を読み込めないというエラーが表示される場合は、最新バージョンの [Microsoft Visual C++ 再頒布可能パッケージ](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) が PC にインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2c738-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="2c738-125">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c738-125">For more information, see:</span></span>
* [<span data-ttu-id="2c738-126">Microsoft spatializer GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="2c738-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="2c738-127">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="2c738-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="2c738-128">Unity のオーディオソースドキュメント</span><span class="sxs-lookup"><span data-stu-id="2c738-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="2c738-129">Unity の spatializer のドキュメント</span><span class="sxs-lookup"><span data-stu-id="2c738-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="2c738-130">距離ベースの減衰</span><span class="sxs-lookup"><span data-stu-id="2c738-130">Distance-based attenuation</span></span>
<span data-ttu-id="2c738-131">Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="2c738-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="2c738-132">これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2c738-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="2c738-133">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c738-133">For more information, see:</span></span>
* <span data-ttu-id="2c738-134">推奨設定のための[混合現実のサウンドデザイン](../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="2c738-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="2c738-135">これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c738-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="2c738-136">ほど</span><span class="sxs-lookup"><span data-stu-id="2c738-136">Reverb</span></span>
<span data-ttu-id="2c738-137">_Microsoft Spatializer_ は、既定で Spatializer 効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="2c738-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="2c738-138">Spatialized ソースに対してリバーブとその他の効果を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="2c738-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="2c738-139">各ソースに **Room 効果の送信レベル** コンポーネントをアタッチする</span><span class="sxs-lookup"><span data-stu-id="2c738-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="2c738-140">各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。</span><span class="sxs-lookup"><span data-stu-id="2c738-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="2c738-141">詳細について [は、spatializer チュートリアルの第5章](tutorials/unity-spatial-audio-ch5.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c738-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="2c738-142">Unity の空間サウンドの例</span><span class="sxs-lookup"><span data-stu-id="2c738-142">Unity spatial sound examples</span></span>
<span data-ttu-id="2c738-143">Unity の空間サウンドの例については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c738-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="2c738-144">MRTK デモ</span><span class="sxs-lookup"><span data-stu-id="2c738-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="2c738-145">[Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="2c738-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2c738-146">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="2c738-146">Next Development Checkpoint</span></span>

<span data-ttu-id="2c738-147">Unity の開発について説明した経験がある場合は、Mixed Reality コアの構成要素を調査しています。</span><span class="sxs-lookup"><span data-stu-id="2c738-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="2c738-148">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="2c738-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c738-149">Text</span><span class="sxs-lookup"><span data-stu-id="2c738-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="2c738-150">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c738-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c738-151">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="2c738-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2c738-152">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="2c738-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c738-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c738-153">See also</span></span>
* [<span data-ttu-id="2c738-154">混合現実におけるサウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="2c738-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="2c738-155">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="2c738-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
