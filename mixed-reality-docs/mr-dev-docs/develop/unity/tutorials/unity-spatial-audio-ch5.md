---
title: 空間オーディオチュートリアル-5。 リバーブを使用して立体オーディオに距離を追加する
description: リバーブ効果を追加して、空間オーディオに対する距離バリエーションの意味を高めます。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、オーディオミキサー、SFX リバーブ
ms.openlocfilehash: d688955910d667edbdb79e63dab16587e66064a4
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679701"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>リバーブを使用して立体オーディオに距離を追加する

## <a name="objectives"></a>目標
前の章では、spatialization をサウンドに追加して、方向を理解できるようにしました。 この5番目の章では、リバーブ効果を追加して、距離を示す音を出します。 目標は次のとおりです。
* リバーブを追加することで、サウンドソースの知覚距離を向上させる
* リスナーとホログラムの距離を使用して、サウンドの知覚距離を制御します。

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>ミキサーグループとリバーブ効果を追加する
[第2章](unity-spatial-audio-ch2.md)では、ミキサーを追加しました。 ミキサーには、既定で **マスター** と呼ばれる **グループ** が1つ含まれています。 一部のサウンドにはリバーブ効果を適用するだけなので、これらのサウンドに対して2番目の **グループ** を追加してみましょう。 **グループ** を追加するには、**オーディオミキサー** で **マスター** グループを右クリックし、[**子グループの追加**] を選択します。

![子グループの追加](images/spatial-audio/add-child-group.png)

この例では、新しいグループに "Room Effect" という名前を付けています。

各 **グループ** には、独自の効果セットがあります。 新しいグループに [ **追加...** ] をクリックし、[ **SFX リバーブ**] を選択して、新しいグループにリバーブ効果を追加します。

![SFX リバーブを追加する](images/spatial-audio/add-sfx-reverb.png)

オーディオの用語では、元の unreverberated オーディオは _ドライパス_ と呼ばれ、リバーブフィルターを使用したフィルター処理後のオーディオは _ウェットパス_ と呼ばれます。 どちらのパスもオーディオ出力に送信され、この混合におけるそれらの相対的な長所は _ウェット/ドライミックス_ と呼ばれます。 ウェットミックスとドライミックスは、距離の意味に強く影響します。

**SFX リバーブ** には、エフェクト内のウェットミックスとドライミックスを調整するためのコントロールが含まれています。 **Microsoft Spatializer** プラグインはドライパスを処理するため、 **SFX リバーブ** はウェットパスに対してのみ使用します。 **SFX リバーブ** の [**インスペクター** ] ウィンドウで、次のようにします。
* [ドライレベル] プロパティを最も低い設定 (-1万 mB) に設定します。
* Room プロパティを最高の設定 (0 mB) に設定します。

これらの変更が完了すると、 **SFX リバーブ** の [**インスペクター** ] ウィンドウは次のようになります。

![SFX リバーブのプロパティ](images/spatial-audio/sfx-reverb-properties.png)

その他の設定は、シミュレートされたルームの感覚を制御します。 特に、 **減衰時間** は、認識される部屋のサイズに関連しています。 

## <a name="enable-reverb-on-the-video-playback"></a>ビデオ再生でリバーブを有効にする
オーディオソースでリバーブを有効にするには、次の2つの手順を実行します。
* **オーディオソース** を適切な **グループ** にルーティングする
* 処理のためにオーディオを **グループ** に渡すように **Microsoft Spatializer** プラグインを設定します

次の手順では、オーディオルーティングを制御するようにスクリプトを調整し、 **Microsoft Spatializer** プラグインに用意されているコントロールスクリプトを添付して、リバーブにデータをフィードします。

**クワッド** の [**インスペクター** ] ウィンドウで、[**コンポーネントの追加**] をクリックし、**ルーム効果の送信レベル** のスクリプトを追加します。

![送信レベルスクリプトの追加](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> **Microsoft Spatializer** プラグインの **ルーム効果の送信レベル** 機能を有効にしない限り、結果の処理のためにオーディオが Unity オーディオエンジンに送信されることはありません。

**Room 効果の送信レベル** コンポーネントには、リバーブ処理のために Unity オーディオエンジンに送信されるオーディオのレベルを設定するグラフコントロールが含まれています。 曲線を下にドラッグして、レベルを約-30dB に設定します。

![リバーブ曲線の調整](images/spatial-audio/adjust-reverb-curve.png)

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

コメント解除これらの行では、スクリプトの [ **インスペクター** ] ペインに2つのプロパティが追加されます。 これらを設定するには、 **Quad** の **Spatialize on Off** コンポーネントの [**インスペクター** ] ウィンドウで次の手順を実行します。
* [ **ルーム効果グループ]** プロパティを新しい部屋効果ミキサーグループに設定します。
* マスター **グループ** プロパティをマスターミキサーグループに設定します

これらの変更が完了すると、 **Spatialize On Off** プロパティは次のようになります。

![Spatialize On Off Extended](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>次のステップ

HoloLens 2 または Unity エディターでアプリを試してみてください。 これで、アプリのボタンにタッチして spatialization をアクティブにすると、スクリプトはビデオのオーディオを部屋の効果グループにルーティングして、リバーブを追加します。 ステレオに切り替えると、オーディオがマスターグループにルーティングされ、リバーブの追加を回避できます。

Unity 用の HoloLens 2 空間オーディオチュートリアルが完了しました。 おめでとうございます。


