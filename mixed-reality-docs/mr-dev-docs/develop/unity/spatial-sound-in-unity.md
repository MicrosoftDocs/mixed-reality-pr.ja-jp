---
title: Unity の立体音響
description: Unity シーン内の特定の3D ポイントから空間サウンドを再生します。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684610"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="3e5b3-104">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="3e5b3-104">Spatial sound in Unity</span></span>

<span data-ttu-id="3e5b3-105">このページでは、Unity の空間サウンドのリソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="3e5b3-106">Spatializer オプション</span><span class="sxs-lookup"><span data-stu-id="3e5b3-106">Spatializer options</span></span>
<span data-ttu-id="3e5b3-107">Mixed reality アプリケーションの Spatializer オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="3e5b3-108">*MS HRTF Spatializer* 。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-108">The *MS HRTF Spatializer* .</span></span> <span data-ttu-id="3e5b3-109">Unity は、これを *Windows Mixed Reality* のオプションパッケージの一部として提供します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="3e5b3-110">これは、高コストの ' 単一ソース ' アーキテクチャの CPU 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="3e5b3-111">これは、元の HoloLens アプリケーションとの下位互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="3e5b3-112">*Microsoft Spatializer* 。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-112">The *Microsoft Spatializer* .</span></span> <span data-ttu-id="3e5b3-113">これは、 [Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="3e5b3-114">これは、低コストの ' マルチソース ' アーキテクチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="3e5b3-115">HoloLens 2 では、これはハードウェアアクセラレータにオフロードされます。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="3e5b3-116">新しいアプリケーションの場合は、 *Microsoft Spatializer* をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-116">For new applications, we recommend the *Microsoft Spatializer* .</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="3e5b3-117">Spatialization を有効にする</span><span class="sxs-lookup"><span data-stu-id="3e5b3-117">Enable spatialization</span></span>

<span data-ttu-id="3e5b3-118">[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して _SpatialAudio_ をインストールし、プロジェクトのオーディオ設定で **microsoft Spatializer** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="3e5b3-119">その後、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-119">Then:</span></span>
* <span data-ttu-id="3e5b3-120">階層内のオブジェクトに **オーディオソース** をアタッチする</span><span class="sxs-lookup"><span data-stu-id="3e5b3-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="3e5b3-121">[ **Enable spatialization** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="3e5b3-122">**空間ブレンド** スライダーを ' 1 ' に移動します</span><span class="sxs-lookup"><span data-stu-id="3e5b3-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="3e5b3-123">開発者ワークステーションで空間オーディオが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="3e5b3-124">これを有効にするには、タスクバーのボリュームアイコンを右クリックし、[空間サウンド] が "オフ" 以外に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="3e5b3-125">HoloLens 2 で聞く内容を最適に表示するには、[ **ヘッドホン用 Windows Sonic** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones** .</span></span>

>[!NOTE]
><span data-ttu-id="3e5b3-126">Unity で、その依存関係の1つが見つからないために SpatialAudio を読み込めないというエラーが表示される場合は、最新バージョンの [Microsoft Visual C++ 再頒布可能パッケージ](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) が PC にインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="3e5b3-127">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-127">For more details, see:</span></span>
* [<span data-ttu-id="3e5b3-128">Microsoft spatializer GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="3e5b3-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="3e5b3-129">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="3e5b3-129">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="3e5b3-130">Unity のオーディオソースドキュメント</span><span class="sxs-lookup"><span data-stu-id="3e5b3-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="3e5b3-131">Unity の spatializer のドキュメント</span><span class="sxs-lookup"><span data-stu-id="3e5b3-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="3e5b3-132">距離ベースの減衰</span><span class="sxs-lookup"><span data-stu-id="3e5b3-132">Distance-based attenuation</span></span>
<span data-ttu-id="3e5b3-133">Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="3e5b3-134">これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="3e5b3-135">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-135">For more details, see:</span></span>
* <span data-ttu-id="3e5b3-136">推奨設定のための[混合現実のサウンドデザイン](../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-136">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="3e5b3-137">これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="3e5b3-138">ほど</span><span class="sxs-lookup"><span data-stu-id="3e5b3-138">Reverb</span></span>
<span data-ttu-id="3e5b3-139">_Microsoft Spatializer_ は、既定で Spatializer 効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="3e5b3-140">Spatialized ソースに対してリバーブとその他の効果を有効にするには:</span><span class="sxs-lookup"><span data-stu-id="3e5b3-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="3e5b3-141">各ソースに **Room 効果の送信レベル** コンポーネントをアタッチする</span><span class="sxs-lookup"><span data-stu-id="3e5b3-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="3e5b3-142">各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="3e5b3-143">詳細について [は、spatializer チュートリアルの第5章](tutorials/unity-spatial-audio-ch5.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-143">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="3e5b3-144">Unity の空間サウンドの例</span><span class="sxs-lookup"><span data-stu-id="3e5b3-144">Unity spatial sound examples</span></span>
<span data-ttu-id="3e5b3-145">Unity の空間サウンドの例については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="3e5b3-146">MRTK デモ</span><span class="sxs-lookup"><span data-stu-id="3e5b3-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="3e5b3-147">[Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="3e5b3-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3e5b3-148">次回の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="3e5b3-148">Next Development Checkpoint</span></span>

<span data-ttu-id="3e5b3-149">ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality コアの構成要素を調査しています。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-149">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="3e5b3-150">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-150">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="3e5b3-151">[[テキスト]](text-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="3e5b3-151">[Text](text-in-unity.md)</span></span>

<span data-ttu-id="3e5b3-152">または、Mixed Reality プラットフォームの機能と Api に移動します。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-152">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3e5b3-153">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="3e5b3-153">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="3e5b3-154">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks) に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="3e5b3-154">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e5b3-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e5b3-155">See also</span></span>
* [<span data-ttu-id="3e5b3-156">混合現実におけるサウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="3e5b3-156">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="3e5b3-157">Microsoft の spatializer チュートリアル</span><span class="sxs-lookup"><span data-stu-id="3e5b3-157">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
