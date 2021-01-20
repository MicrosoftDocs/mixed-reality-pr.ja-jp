---
title: 空間オーディオチュートリアル-5。 リバーブを使用して立体オーディオに距離を追加する
description: リバーブ効果を追加して、空間オーディオに対する距離バリエーションの意味を高めます。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、オーディオミキサー、SFX リバーブ
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578383"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="86885-105">5.リバーブを使用して立体オーディオに距離を追加する</span><span class="sxs-lookup"><span data-stu-id="86885-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="86885-106">概要</span><span class="sxs-lookup"><span data-stu-id="86885-106">Overview</span></span>

<span data-ttu-id="86885-107">前のチュートリアルでは、サウンドに対して spatialization を追加して、このチュートリアルの方向を理解できるようにしました。このチュートリアルでは、音声を表示するためのリバーブ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="86885-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="86885-108">目標</span><span class="sxs-lookup"><span data-stu-id="86885-108">Objectives</span></span>

* <span data-ttu-id="86885-109">リバーブを追加することで、サウンドソースの知覚距離を改善します。</span><span class="sxs-lookup"><span data-stu-id="86885-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="86885-110">リスナーとホログラムの距離を使用して、サウンドの知覚距離を制御します。</span><span class="sxs-lookup"><span data-stu-id="86885-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="86885-111">ミキサーグループとリバーブ効果を追加する</span><span class="sxs-lookup"><span data-stu-id="86885-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="86885-112">[Spatializing button 対話サウンドチュートリアル](unity-spatial-audio-ch2.md)では、ミキサーを追加しました。</span><span class="sxs-lookup"><span data-stu-id="86885-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="86885-113">ミキサーには、既定で **マスター** と呼ばれる **グループ** が1つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="86885-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="86885-114">一部のサウンドにはリバーブ効果を適用するだけなので、これらのサウンドに対して2番目のグループを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="86885-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="86885-115">グループを追加するには、 **オーディオミキサー** でマスターグループを右クリックし、[ **子グループの追加** ] を選択し、適切な名前を指定します。たとえば、「 _部屋の効果_:</span><span class="sxs-lookup"><span data-stu-id="86885-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![子グループの追加](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="86885-117">各 **グループ** には、独自の効果セットがあります。</span><span class="sxs-lookup"><span data-stu-id="86885-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="86885-118">新しいグループに [ **追加...** ] をクリックし、[ **SFX リバーブ**] を選択して、新しいグループにリバーブ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="86885-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX リバーブを追加する](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="86885-120">オーディオの用語では、元の unreverberated オーディオは _ドライパス_ と呼ばれ、リバーブフィルターを使用したフィルター処理後のオーディオは _ウェットパス_ と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="86885-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="86885-121">どちらのパスもオーディオ出力に送信され、この混合におけるそれらの相対的な長所は _ウェット/ドライミックス_ と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="86885-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="86885-122">ウェットミックスとドライミックスは、距離の意味に強く影響します。</span><span class="sxs-lookup"><span data-stu-id="86885-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="86885-123">**SFX リバーブ** には、エフェクト内のウェットミックスとドライミックスを調整するためのコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86885-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="86885-124">**Microsoft Spatializer** プラグインはドライパスを処理するため、 **SFX リバーブ** はウェットパスに対してのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="86885-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="86885-125">**SFX リバーブ** の [インスペクター] ウィンドウで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="86885-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="86885-126">[ **ドライレベル** ] プロパティを最も低い設定 (-1万 mB) に設定します。</span><span class="sxs-lookup"><span data-stu-id="86885-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="86885-127">**Room プロパティ** を最高の設定 (0 mB) に設定します。</span><span class="sxs-lookup"><span data-stu-id="86885-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX リバーブのプロパティ](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="86885-129">その他の設定は、シミュレートされたルームの感覚を制御します。</span><span class="sxs-lookup"><span data-stu-id="86885-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="86885-130">特に、 **減衰時間** は、認識される部屋のサイズに関連しています。</span><span class="sxs-lookup"><span data-stu-id="86885-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="86885-131">ビデオ再生でリバーブを有効にする</span><span class="sxs-lookup"><span data-stu-id="86885-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="86885-132">オーディオソースでリバーブを有効にするには、次の2つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="86885-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="86885-133">**オーディオソース** を適切な **グループ** にルーティングする</span><span class="sxs-lookup"><span data-stu-id="86885-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="86885-134">処理のためにオーディオを **グループ** に渡すように **Microsoft Spatializer** プラグインを設定します</span><span class="sxs-lookup"><span data-stu-id="86885-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="86885-135">次の手順では、オーディオルーティングを制御するようにスクリプトを調整し、 **Microsoft Spatializer** プラグインに用意されているコントロールスクリプトを添付して、リバーブにデータをフィードします。</span><span class="sxs-lookup"><span data-stu-id="86885-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="86885-136">階層で **クワッド** を選択した状態で、[インスペクター] ウィンドウの [ **コンポーネントの追加** ] をクリックし、 **ルーム効果の送信レベル (スクリプト)** を追加します。</span><span class="sxs-lookup"><span data-stu-id="86885-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![送信レベルスクリプトの追加](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="86885-138">**Microsoft Spatializer** プラグインの **ルーム効果の送信レベル** 機能を有効にしない限り、結果の処理のためにオーディオが Unity オーディオエンジンに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="86885-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="86885-139">**Room 効果の送信レベル** コンポーネントには、リバーブ処理のために Unity オーディオエンジンに送信されるオーディオのレベルを設定するグラフコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86885-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="86885-140">グラフコントロールを開くには、 **ルーム効果の送信レベル** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86885-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="86885-141">緑の曲線を下にドラッグして、レベルを約-30 Db に設定します。</span><span class="sxs-lookup"><span data-stu-id="86885-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![リバーブ曲線の調整](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="86885-143">次に、 **SpatializeOnOff** スクリプトの4つのコメント行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="86885-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="86885-144">スクリプトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="86885-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="86885-145">これらの行をコメント解除すると、 **SpatializeOnOff スクリプト** のインスペクターに2つのプロパティが追加されます。</span><span class="sxs-lookup"><span data-stu-id="86885-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="86885-146">これらは、**クワッド** の **SpatializeOnOff** コンポーネントのインスペクターウィンドウで割り当てます。</span><span class="sxs-lookup"><span data-stu-id="86885-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="86885-147">階層で Quad オブジェクトを選択した状態で、[インスペクター] ウィンドウで **SpatializeOnOff スクリプト** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="86885-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="86885-148">[ **ルーム効果グループ]** プロパティを新しい部屋効果ミキサーグループに設定します。</span><span class="sxs-lookup"><span data-stu-id="86885-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="86885-149">マスター **グループ** プロパティをマスターミキサーグループに設定します</span><span class="sxs-lookup"><span data-stu-id="86885-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="86885-151">結論</span><span class="sxs-lookup"><span data-stu-id="86885-151">Congratulations</span></span>

<span data-ttu-id="86885-152">Unity 用の HoloLens 2 空間オーディオチュートリアルが完了しました。</span><span class="sxs-lookup"><span data-stu-id="86885-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="86885-153">HoloLens 2 または Unity でアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="86885-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="86885-154">アプリのボタンをクリックして spatialization をアクティブ化すると、スクリプトはビデオのオーディオを部屋の効果グループにルーティングして、リバーブを追加します。</span><span class="sxs-lookup"><span data-stu-id="86885-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="86885-155">ステレオに切り替えると、オーディオがマスターグループにルーティングされ、リバーブの追加を回避できます。</span><span class="sxs-lookup"><span data-stu-id="86885-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="86885-156">HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86885-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
