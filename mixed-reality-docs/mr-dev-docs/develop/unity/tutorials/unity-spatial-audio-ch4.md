---
title: 空間オーディオチュートリアル-4. 実行時の立体オーディオの有効化と無効化
description: ボタンを使用して、実行時に spatialization のオーディオを有効または無効にします。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590734"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="5a50b-105">4. 実行時に spatialization を有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="5a50b-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="5a50b-106">概要</span><span class="sxs-lookup"><span data-stu-id="5a50b-106">Overview</span></span>

<span data-ttu-id="5a50b-107">このチュートリアルでは、実行時に spatialization を有効または無効にし、unity エディターと HoloLens 2 でこれをテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="5a50b-108">目標</span><span class="sxs-lookup"><span data-stu-id="5a50b-108">Objectives</span></span>

* <span data-ttu-id="5a50b-109">Game オブジェクトの spatialization を制御する新しいスクリプトを追加します</span><span class="sxs-lookup"><span data-stu-id="5a50b-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="5a50b-110">ボタンの操作から spatialization コントロールスクリプトを駆動する</span><span class="sxs-lookup"><span data-stu-id="5a50b-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="5a50b-111">Spatialization コントロールスクリプトの追加</span><span class="sxs-lookup"><span data-stu-id="5a50b-111">Add spatialization control script</span></span>

 <span data-ttu-id="5a50b-112">プロジェクトウィンドウ内を右クリックし、[c# スクリプトの **作成**] を選択して  >  新しい c# スクリプトを作成し、スクリプトに適切な名前 (たとえば、 _SpatializeOnOff_) を入力します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![スクリプトの作成](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="5a50b-114">プロジェクトウィンドウでスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="5a50b-115">既定のスクリプトの内容を次の内容に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="5a50b-116">スクリプトのいくつかの行がコメントアウトされています。これらの行は、 [次の章「リバーブを使用した空間オーディオへの距離の追加](unity-spatial-audio-ch5.md)」でコメント解除されます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="5a50b-117">Spatialization を有効または無効にするために、スクリプトは **spatialBlend** プロパティを調整するだけで、 **spatialization** プロパティを有効のままにします。</span><span class="sxs-lookup"><span data-stu-id="5a50b-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="5a50b-118">このモードでは、Unity でも **ボリューム** 曲線が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="5a50b-119">そうしないと、ユーザーがソースから遠くに spatialization を無効にした場合に、音量が急激に増加していることが聞こえます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="5a50b-120">Spatialization を完全に無効にする場合は、 **SourceObject** 変数の **spatialization** boolean プロパティも調整するようにスクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="5a50b-121">スクリプトをアタッチして、ボタンからドライブを作成します</span><span class="sxs-lookup"><span data-stu-id="5a50b-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="5a50b-122">階層で [ **Quad** ] を選択し、[インスペクター] ウィンドウで [コンポーネントの追加] ボタンを使用して **SpatializeOnOff (スクリプト)** を追加します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![スクリプトをクワッドに追加する](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="5a50b-124">階層で、 **PressableButtonHoloLens2**  >  **iconandtext**  >  **TextMeshPro** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="5a50b-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="5a50b-125">階層で **Quad** オブジェクトを選択した状態で、[インスペクター] ウィンドウで **Spatialize On Off (スクリプト)** コンポーネントを見つけ、PressableButtonHoloLens2 の **TextMeshPro** コンポーネントをドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="5a50b-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![階層内の PressableButtonHoloLens2 オブジェクトを検索する](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="5a50b-127">ボタンが離されたときに **SpatializeOnOff** スクリプトを呼び出すようにボタンを設定するには、対話型スクリプトを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a50b-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="5a50b-128">[階層] ウィンドウで、[ **PressableButtonHoloLens2**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="5a50b-129">[インスペクター] ウィンドウで、 **対話型 (スクリプト)** コンポーネントを見つけて、[OnClick () イベント] の下にある [+] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a50b-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="5a50b-130">[階層] ウィンドウで **PressableButtonHoloLens2** オブジェクトを選択した状態で、[階層] ウィンドウから、 **Quad** オブジェクトをクリックして、追加したイベントの空の **None (オブジェクト)** フィールドにドラッグします。このボタンをクリックすると、ボタンのクリックイベントをこのボタンでリッスンするようになります。</span><span class="sxs-lookup"><span data-stu-id="5a50b-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="5a50b-131">同じイベントの **[No Function]\(関数なし\)** ドロップダウンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a50b-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="5a50b-132">次に、[ **SpatializeOnOff**  >  **SwapSpatialization ()** ] を選択して、空間オーディオをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="5a50b-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![ボタンの操作の設定](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="5a50b-134">結論</span><span class="sxs-lookup"><span data-stu-id="5a50b-134">Congratulations</span></span>

<span data-ttu-id="5a50b-135">このチュートリアルでは、実行時に spatialization を有効または無効にする方法、HoloLens 2 または Unity エディターでアプリをテストする方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="5a50b-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="5a50b-136">アプリで、ボタンをクリックして、オーディオの spatialization をアクティブ化および非アクティブ化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5a50b-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="5a50b-137">次のチュートリアルでは、音声による距離を示すリバーブ効果を追加します。</span><span class="sxs-lookup"><span data-stu-id="5a50b-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="5a50b-138">HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a50b-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a50b-139">次のチュートリアル: 5. リバーブを使用して空間オーディオに距離を追加する</span><span class="sxs-lookup"><span data-stu-id="5a50b-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
