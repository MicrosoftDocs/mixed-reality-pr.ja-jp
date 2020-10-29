---
title: 空間オーディオチュートリアル-5。 リバーブを使用して立体オーディオに距離を追加する
description: リバーブ効果を追加して、空間オーディオに対する距離バリエーションの意味を高めます。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91689674"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="7f48f-105">リバーブを使用して立体オーディオに距離を追加する</span><span class="sxs-lookup"><span data-stu-id="7f48f-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="7f48f-106">目標</span><span class="sxs-lookup"><span data-stu-id="7f48f-106">Objectives</span></span>
<span data-ttu-id="7f48f-107">前の章では、spatialization をサウンドに追加して、方向を理解できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="7f48f-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="7f48f-108">この5番目の章では、リバーブ効果を追加して、距離を示す音を出します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="7f48f-109">目標は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7f48f-109">Our objectives are to:</span></span>
* <span data-ttu-id="7f48f-110">リバーブを追加することで、サウンドソースの知覚距離を向上させる</span><span class="sxs-lookup"><span data-stu-id="7f48f-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="7f48f-111">リスナーとホログラムの距離を使用して、サウンドの知覚距離を制御します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="7f48f-112">ミキサーグループとリバーブ効果を追加する</span><span class="sxs-lookup"><span data-stu-id="7f48f-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="7f48f-113">[第2章](unity-spatial-audio-ch2.md)では、ミキサーを追加しました。</span><span class="sxs-lookup"><span data-stu-id="7f48f-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="7f48f-114">ミキサーには、既定で **マスター** と呼ばれる **グループ** が1つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f48f-114">The mixer includes one **Group** by default called **Master** .</span></span> <span data-ttu-id="7f48f-115">一部のサウンドにはリバーブ効果を適用するだけなので、これらのサウンドに対して2番目の **グループ** を追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="7f48f-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="7f48f-116">**グループ** を追加するには、 **オーディオミキサー** で **マスター** グループを右クリックし、[ **子グループの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-116">To add a **Group** , right click on the **Master** group in the **Audio Mixer** and choose **Add child group** :</span></span>

![子グループの追加](images/spatial-audio/add-child-group.png)

<span data-ttu-id="7f48f-118">この例では、新しいグループに "Room Effect" という名前を付けています。</span><span class="sxs-lookup"><span data-stu-id="7f48f-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="7f48f-119">各 **グループ** には、独自の効果セットがあります。</span><span class="sxs-lookup"><span data-stu-id="7f48f-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="7f48f-120">新しいグループに [ **追加...** ] をクリックし、[ **SFX リバーブ** ] を選択して、新しいグループにリバーブ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb** :</span></span>

![SFX リバーブを追加する](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="7f48f-122">オーディオの用語では、元の unreverberated オーディオは _ドライパス_ と呼ばれ、リバーブフィルターを使用したフィルター処理後のオーディオは _ウェットパス_ と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7f48f-122">In audio terminology, the original, unreverberated audio is called the _dry path_ , and the audio after filtering with the reverb filter is called the _wet path_ .</span></span> <span data-ttu-id="7f48f-123">どちらのパスもオーディオ出力に送信され、この混合におけるそれらの相対的な長所は _ウェット/ドライミックス_ と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7f48f-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_ .</span></span> <span data-ttu-id="7f48f-124">ウェットミックスとドライミックスは、距離の意味に強く影響します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="7f48f-125">**SFX リバーブ** には、エフェクト内のウェットミックスとドライミックスを調整するためのコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f48f-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="7f48f-126">**Microsoft Spatializer** プラグインはドライパスを処理するため、 **SFX リバーブ** はウェットパスに対してのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="7f48f-127">**SFX リバーブ** の [ **インスペクター** ] ウィンドウで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7f48f-127">On the **Inspector** pane of your **SFX Reverb** :</span></span>
* <span data-ttu-id="7f48f-128">[ドライレベル] プロパティを最も低い設定 (-1万 mB) に設定します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="7f48f-129">Room プロパティを最高の設定 (0 mB) に設定します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="7f48f-130">これらの変更が完了すると、 **SFX リバーブ** の [ **インスペクター** ] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7f48f-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![SFX リバーブのプロパティ](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="7f48f-132">その他の設定は、シミュレートされたルームの感覚を制御します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="7f48f-133">特に、 **減衰時間** は、認識される部屋のサイズに関連しています。</span><span class="sxs-lookup"><span data-stu-id="7f48f-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="7f48f-134">ビデオ再生でリバーブを有効にする</span><span class="sxs-lookup"><span data-stu-id="7f48f-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="7f48f-135">オーディオソースでリバーブを有効にするには、次の2つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="7f48f-136">**オーディオソース** を適切な **グループ** にルーティングする</span><span class="sxs-lookup"><span data-stu-id="7f48f-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="7f48f-137">処理のためにオーディオを **グループ** に渡すように **Microsoft Spatializer** プラグインを設定します</span><span class="sxs-lookup"><span data-stu-id="7f48f-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="7f48f-138">次の手順では、オーディオルーティングを制御するようにスクリプトを調整し、 **Microsoft Spatializer** プラグインに用意されているコントロールスクリプトを添付して、リバーブにデータをフィードします。</span><span class="sxs-lookup"><span data-stu-id="7f48f-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="7f48f-139">**クワッド** の [ **インスペクター** ] ウィンドウで、[ **コンポーネントの追加** ] をクリックし、 **ルーム効果の送信レベル** のスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-139">On the **Inspector** pane for the **Quad** , click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![送信レベルスクリプトの追加](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="7f48f-141">**Microsoft Spatializer** プラグインの **ルーム効果の送信レベル** 機能を有効にしない限り、結果の処理のためにオーディオが Unity オーディオエンジンに送信されることはありません。</span><span class="sxs-lookup"><span data-stu-id="7f48f-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="7f48f-142">**Room 効果の送信レベル** コンポーネントには、リバーブ処理のために Unity オーディオエンジンに送信されるオーディオのレベルを設定するグラフコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f48f-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="7f48f-143">曲線を下にドラッグして、レベルを約-30dB に設定します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![リバーブ曲線の調整](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="7f48f-145">次に、 **SpatializeOnOff** スクリプトの4つのコメント行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="7f48f-146">スクリプトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7f48f-146">The script will now look like this:</span></span>
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

<span data-ttu-id="7f48f-147">コメント解除これらの行では、スクリプトの [ **インスペクター** ] ペインに2つのプロパティが追加されます。</span><span class="sxs-lookup"><span data-stu-id="7f48f-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="7f48f-148">これらを設定するには、 **Quad** の **Spatialize on Off** コンポーネントの [ **インスペクター** ] ウィンドウで次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad** :</span></span>
* <span data-ttu-id="7f48f-149">[ **ルーム効果グループ]** プロパティを新しい部屋効果ミキサーグループに設定します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="7f48f-150">マスター **グループ** プロパティをマスターミキサーグループに設定します</span><span class="sxs-lookup"><span data-stu-id="7f48f-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="7f48f-151">これらの変更が完了すると、 **Spatialize On Off** プロパティは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7f48f-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatialize On Off Extended](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="7f48f-153">次のステップ</span><span class="sxs-lookup"><span data-stu-id="7f48f-153">Next steps</span></span>

<span data-ttu-id="7f48f-154">HoloLens 2 または Unity エディターでアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="7f48f-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="7f48f-155">これで、アプリのボタンにタッチして spatialization をアクティブにすると、スクリプトはビデオのオーディオを部屋の効果グループにルーティングして、リバーブを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f48f-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="7f48f-156">ステレオに切り替えると、オーディオがマスターグループにルーティングされ、リバーブの追加を回避できます。</span><span class="sxs-lookup"><span data-stu-id="7f48f-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="7f48f-157">Unity 用の HoloLens 2 空間オーディオチュートリアルが完了しました。</span><span class="sxs-lookup"><span data-stu-id="7f48f-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="7f48f-158">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="7f48f-158">Congratulations!</span></span>


