---
title: 空間オーディオチュートリアル-5。 リバーブを使用して立体オーディオに距離を追加する
description: リバーブ効果を追加して、空間オーディオに対する距離バリエーションの意味を高めます。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、オーディオミキサー、SFX リバーブ
ms.openlocfilehash: f7a5270d969f2e462db0244bd6c68b99347ae1a7
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590724"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5.リバーブを使用して立体オーディオに距離を追加する

## <a name="overview"></a>概要

前のチュートリアルでは、サウンドに対して spatialization を追加して、このチュートリアルの方向を理解できるようにしました。このチュートリアルでは、音声を表示するためのリバーブ効果を追加します。

## <a name="objectives"></a>目標

* リバーブを追加することで、サウンドソースの知覚距離を改善します。
* リスナーとホログラムの距離を使用して、サウンドの知覚距離を制御します。

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>ミキサーグループとリバーブ効果を追加する

[Spatializing button 対話サウンドチュートリアル](unity-spatial-audio-ch2.md)では、ミキサーを追加しました。 ミキサーには、既定で **マスター** と呼ばれる **グループ** が1つ含まれています。 一部のサウンドにはリバーブ効果を適用するだけなので、これらのサウンドに対して2番目のグループを追加してみましょう。 グループを追加するには、 **オーディオミキサー** でマスターグループを右クリックし、[ **子グループの追加** ] を選択し、適切な名前を指定します。たとえば、「 _部屋の効果_:

![子グループの追加](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

各 **グループ** には、独自の効果セットがあります。 新しいグループに [ **追加...** ] をクリックし、[ **SFX リバーブ**] を選択して、新しいグループにリバーブ効果を追加します。

![SFX リバーブを追加する](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

オーディオの用語では、元の unreverberated オーディオは _ドライパス_ と呼ばれ、リバーブフィルターを使用したフィルター処理後のオーディオは _ウェットパス_ と呼ばれます。 どちらのパスもオーディオ出力に送信され、この混合におけるそれらの相対的な長所は _ウェット/ドライミックス_ と呼ばれます。 ウェットミックスとドライミックスは、距離の意味に強く影響します。

**SFX リバーブ** には、エフェクト内のウェットミックスとドライミックスを調整するためのコントロールが含まれています。 **Microsoft Spatializer** プラグインはドライパスを処理するため、 **SFX リバーブ** はウェットパスに対してのみ使用します。 **SFX リバーブ** の [インスペクター] ウィンドウで、次のようにします。

* [ **ドライレベル** ] プロパティを最も低い設定 (-1万 mB) に設定します。
* **Room プロパティ** を最高の設定 (0 mB) に設定します。

![SFX リバーブのプロパティ](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

その他の設定は、シミュレートされたルームの感覚を制御します。 特に、 **減衰時間** は、認識される部屋のサイズに関連しています。

## <a name="enable-reverb-on-the-video-playback"></a>ビデオ再生でリバーブを有効にする

オーディオソースでリバーブを有効にするには、次の2つの手順を実行します。

* **オーディオソース** を適切な **グループ** にルーティングする
* 処理のためにオーディオを **グループ** に渡すように **Microsoft Spatializer** プラグインを設定します

次の手順では、オーディオルーティングを制御するようにスクリプトを調整し、 **Microsoft Spatializer** プラグインに用意されているコントロールスクリプトを添付して、リバーブにデータをフィードします。

階層で **クワッド** を選択した状態で、[インスペクター] ウィンドウの [ **コンポーネントの追加** ] をクリックし、 **ルーム効果の送信レベル (スクリプト)** を追加します。

![送信レベルスクリプトの追加](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> **Microsoft Spatializer** プラグインの **ルーム効果の送信レベル** 機能を有効にしない限り、結果の処理のためにオーディオが Unity オーディオエンジンに送信されることはありません。

**Room 効果の送信レベル** コンポーネントには、リバーブ処理のために Unity オーディオエンジンに送信されるオーディオのレベルを設定するグラフコントロールが含まれています。 グラフコントロールを開くには、 **ルーム効果の送信レベル** をクリックします。  緑の曲線を下にドラッグして、レベルを約-30 Db に設定します。

![リバーブ曲線の調整](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

次に、 **SpatializeOnOff** スクリプトの4つのコメント行のコメントを解除します。 スクリプトは次のようになります。

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

これらの行をコメント解除すると、 **SpatializeOnOff スクリプト** のインスペクターに2つのプロパティが追加されます。 これらは、**クワッド** の **SpatializeOnOff** コンポーネントのインスペクターウィンドウで割り当てます。

階層で Quad オブジェクトを選択した状態で、[インスペクター] ウィンドウで **SpatializeOnOff スクリプト** コンポーネントを見つけます。

* [ **ルーム効果グループ]** プロパティを新しい部屋効果ミキサーグループに設定します。
* マスター **グループ** プロパティをマスターミキサーグループに設定します

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>結論

Unity 用の HoloLens 2 空間オーディオチュートリアルが完了しました。 HoloLens 2 または Unity でアプリを試してみてください。 アプリのボタンをクリックして spatialization をアクティブ化すると、スクリプトはビデオのオーディオを部屋の効果グループにルーティングして、リバーブを追加します。 ステレオに切り替えると、オーディオがマスターグループにルーティングされ、リバーブの追加を回避できます。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。
