---
title: 空間オーディオチュートリアル-4. 実行時の立体オーディオの有効化と無効化
description: ボタンを使用して、実行時に spatialization のオーディオを有効または無効にします。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: c9e510e544962c5d1a4c462d20dafa222c6a5289
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002607"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="3466a-105">実行時の spatialization の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="3466a-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="3466a-106">目標</span><span class="sxs-lookup"><span data-stu-id="3466a-106">Objectives</span></span>
<span data-ttu-id="3466a-107">この4番目の章では、次のことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3466a-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="3466a-108">Game オブジェクトの spatialization を制御する新しいスクリプトを追加します</span><span class="sxs-lookup"><span data-stu-id="3466a-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="3466a-109">ボタンの操作から spatialization コントロールスクリプトを駆動する</span><span class="sxs-lookup"><span data-stu-id="3466a-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="3466a-110">Spatialization コントロールスクリプトの追加</span><span class="sxs-lookup"><span data-stu-id="3466a-110">Add spatialization control script</span></span>
<span data-ttu-id="3466a-111">**プロジェクト** ペイン内を右クリックし、[ **Create-> c# スクリプト**] を選択して新しい c# スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3466a-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="3466a-112">スクリプトに "SpatializeOnOff" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3466a-112">Name your script "SpatializeOnOff".</span></span>

![スクリプトの作成](images/spatial-audio/create-script.png)

<span data-ttu-id="3466a-114">**プロジェクト** ウィンドウでスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3466a-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="3466a-115">既定のスクリプトの内容を次の内容に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3466a-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="3466a-116">スクリプトのいくつかの行がコメントアウトされています。これらの行は、 [5 章](unity-spatial-audio-ch5.md)でコメント解除されます。</span><span class="sxs-lookup"><span data-stu-id="3466a-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="3466a-117">Spatialization を有効または無効にするために、スクリプトは **spatialBlend** プロパティを調整するだけで、 **spatialization** プロパティを有効のままにします。</span><span class="sxs-lookup"><span data-stu-id="3466a-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="3466a-118">このモードでは、Unity でも **ボリューム** 曲線が適用されます。</span><span class="sxs-lookup"><span data-stu-id="3466a-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="3466a-119">そうしないと、ユーザーがソースから遠くに spatialization を無効にした場合に、音量が急激に増加していることが聞こえます。</span><span class="sxs-lookup"><span data-stu-id="3466a-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="3466a-120">Spatialization を完全に無効にする場合は、 **SourceObject** 変数の **spatialization** boolean プロパティも調整するようにスクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="3466a-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="3466a-121">スクリプトをアタッチして、ボタンからドライブを作成します</span><span class="sxs-lookup"><span data-stu-id="3466a-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="3466a-122">**クワッド** の [**インスペクター** ] ウィンドウで、[**コンポーネントの追加**] をクリックし、 **Spatialize On Off** スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="3466a-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![スクリプトをクワッドに追加する](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="3466a-124">**クワッド** の **Spatialize on Off** コンポーネントで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="3466a-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="3466a-125">**階層** で **PressableButtonHoloLens2-> iconandtext-> TextMeshPro** subject を見つけます。</span><span class="sxs-lookup"><span data-stu-id="3466a-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![階層内の PressableButtonHoloLens2 オブジェクトを検索する](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="3466a-127">**TextMeshPro** Subject を **Spatialize On Off** コンポーネントの **buttontextobject** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3466a-127">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="3466a-128">これらの変更が完了すると、 **Quad** の **Spatialize** コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3466a-128">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on off basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="3466a-130">ボタンが離されたときに **Spatialize On Off** スクリプトを呼び出すようにボタンを設定するには、 **PressableButtonHoloLens2** オブジェクトの [**インスペクター** ] ペインを開き、**対話型** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="3466a-130">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="3466a-131">**Events** サブセクションの **OnClick ()** 領域を検索します。</span><span class="sxs-lookup"><span data-stu-id="3466a-131">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="3466a-132">**階層** からターゲットオブジェクトスロットに **クワッド** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3466a-132">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="3466a-133">[アクション] ボックスの一覧から [ **SpatializeOnOff** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3466a-133">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="3466a-134">これらの変更が完了すると、 **対話型** コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3466a-134">After these changes, the **Interactable** component will look like this:</span></span>

![ボタンの操作の設定](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="3466a-136">次のステップ</span><span class="sxs-lookup"><span data-stu-id="3466a-136">Next steps</span></span>
<span data-ttu-id="3466a-137">HoloLens 2 または Unity エディターでアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="3466a-137">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="3466a-138">アプリで、ボタンをタッチして、ビデオの spatialization をアクティブ化および非アクティブ化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3466a-138">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="3466a-139">Unity エディターでテストする場合は、スペースバーを押し、スクロールホイールを使用してスクロールし、ハンドシミュレーションをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="3466a-139">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3466a-140">章5</span><span class="sxs-lookup"><span data-stu-id="3466a-140">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

