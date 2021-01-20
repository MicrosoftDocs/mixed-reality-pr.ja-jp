---
title: 空間オーディオチュートリアル-4. 実行時の立体オーディオの有効化と無効化
description: ボタンを使用して、実行時に spatialization のオーディオを有効または無効にします。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: 9239c45efa5196b94fe2e05f85a2e83df6c7789f
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578321"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. 実行時に spatialization を有効または無効にする

## <a name="overview"></a>概要

このチュートリアルでは、実行時に spatialization を有効または無効にし、unity エディターと HoloLens 2 でこれをテストする方法について説明します。

## <a name="objectives"></a>目標

* Game オブジェクトの spatialization を制御する新しいスクリプトを追加します
* ボタンの操作から spatialization コントロールスクリプトを駆動する

## <a name="add-spatialization-control-script"></a>Spatialization コントロールスクリプトの追加

 プロジェクトウィンドウ内を右クリックし、[c# スクリプトの **作成**] を選択して  >  新しい c# スクリプトを作成し、スクリプトに適切な名前 (たとえば、 _SpatializeOnOff_) を入力します。

![スクリプトの作成](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

プロジェクトウィンドウでスクリプトをダブルクリックして、Visual Studio で開きます。 既定のスクリプトの内容を次の内容に置き換えます。

> [!NOTE]
> スクリプトのいくつかの行がコメントアウトされています。これらの行は、 [次の章「リバーブを使用した空間オーディオへの距離の追加](unity-spatial-audio-ch5.md)」でコメント解除されます。

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
> Spatialization を有効または無効にするために、スクリプトは **spatialBlend** プロパティを調整するだけで、 **spatialization** プロパティを有効のままにします。 このモードでは、Unity でも **ボリューム** 曲線が適用されます。 そうしないと、ユーザーがソースから遠くに spatialization を無効にした場合に、音量が急激に増加していることが聞こえます。
> Spatialization を完全に無効にする場合は、 **SourceObject** 変数の **spatialization** boolean プロパティも調整するようにスクリプトを変更します。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>スクリプトをアタッチして、ボタンからドライブを作成します

階層で [ **Quad** ] を選択し、[インスペクター] ウィンドウで [コンポーネントの追加] ボタンを使用して **SpatializeOnOff (スクリプト)** を追加します。

![スクリプトをクワッドに追加する](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

階層で、 **PressableButtonHoloLens2**  >  **iconandtext**  >  **TextMeshPro** を見つけます。

階層で **Quad** オブジェクトを選択した状態で、[インスペクター] ウィンドウで **Spatialize On Off (スクリプト)** コンポーネントを見つけ、PressableButtonHoloLens2 の **TextMeshPro** コンポーネントをドラッグアンドドロップします。

![階層内の PressableButtonHoloLens2 オブジェクトを検索する](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

ボタンが離されたときに **SpatializeOnOff** スクリプトを呼び出すようにボタンを設定するには、対話型スクリプトを構成する必要があります。

[階層] ウィンドウで、[ **PressableButtonHoloLens2**] を選択します。 [インスペクター] ウィンドウで、 **対話型 (スクリプト)** コンポーネントを見つけて、[OnClick () イベント] の下にある [+] アイコンをクリックします。

* [階層] ウィンドウで **PressableButtonHoloLens2** オブジェクトを選択した状態で、[階層] ウィンドウから、 **Quad** オブジェクトをクリックして、追加したイベントの空の **None (オブジェクト)** フィールドにドラッグします。このボタンをクリックすると、ボタンのクリックイベントをこのボタンでリッスンするようになります。

* 同じイベントの **[No Function]\(関数なし\)** ドロップダウンをクリックします。 次に、[ **SpatializeOnOff**  >  **SwapSpatialization ()** ] を選択して、空間オーディオをオンまたはオフにします。

![ボタンの操作の設定](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、実行時に spatialization を有効または無効にする方法、HoloLens 2 または Unity エディターでアプリをテストする方法を学習しました。 アプリで、ボタンをクリックして、オーディオの spatialization をアクティブ化および非アクティブ化できるようになりました。

次のチュートリアルでは、音声による距離を示すリバーブ効果を追加します。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。

> [!div class="nextstepaction"]
> [次のチュートリアル: 5. リバーブを使用して空間オーディオに距離を追加する](unity-spatial-audio-ch5.md)
