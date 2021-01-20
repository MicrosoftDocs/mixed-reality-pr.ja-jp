---
title: MR の基本 101E - エミュレーターを使用した完全なプロジェクト
description: Unity、Visual Studio、および HoloLens Emulator を使用したこのコーディングのチュートリアルに従って、holographic アプリケーションの基本を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、ホログラム、academy、チュートリアル、エミュレーター、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、仮想リアリティヘッドセット、windows 10、宝石、ジェスチャ、音声入力、空間サウンド、空間マッピング
ms.openlocfilehash: afe62dbc3385b41d08011bf7893672272f25485b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583698"
---
# <a name="mr-basics-101e-complete-project-with-emulator"></a>MR の基本 101E:エミュレーターを使用した完全なプロジェクト

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](mrlearning-base.md)が投稿されています。

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

このチュートリアルでは、Unity でビルドされた完全なプロジェクトについて説明します。これは、 [宝石](../../../design/gaze-and-commit.md)、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)、 [音声入力](../../../design/voice-input.md)、 [空間サウンド](../../../design/spatial-sound.md) 、 [空間マッピング](../../../design/spatial-mapping.md)など、HoloLens のコア Windows Mixed Reality 機能を示しています。 このチュートリアルの完了には約1時間かかります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR の基本 101E:エミュレーターを使用した完全なプロジェクト</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>前提条件

* 適切な [ツールがインストール](../../install-the-tools.md)された WINDOWS 10 PC。

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) をダウンロードします。 Unity 2017.2 以降が必要です。
  * 引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)をご利用ください。
  * 引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)をご利用ください。
  * 引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)をご利用ください。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。 フォルダー名は **Origami** のままにしておきます。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)ます。

## <a name="chapter-1---holo-world"></a>Chapter 1-"Holo" ワールド

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。

### <a name="objectives"></a>目標

* Holographic 開発用に Unity を設定します。
* ホログラムを作成します。
* 作成したホログラムを確認します。

### <a name="instructions"></a>Instructions

* Unity を起動します。
* **[Open]** を選択します。
* 前にアーカイブしていない **Origami** フォルダーとして場所を入力します。
* [ **Origami** ] を選択し、[ **フォルダーの選択**] をクリックします。
* 新しいシーンを保存します。 [**ファイル**  /  **名を付けてシーンを保存** する。
* シーンに **Origami** という名前を **付け** 、[保存] ボタンを押します。

#### <a name="setup-the-main-camera"></a>メインカメラの設定

* **[Hierarchy]\(階層\) パネル** で、 **[Main Camera]\(メイン カメラ\)** を選択します。
* **インスペクター** で、変換位置を **0、0、0** に設定します。
* " **Clear Flags** " プロパティを見つけ、ドロップ **ダウンから [** **単色**] に変更します。
* **[Background]\(背景\)** フィールドをクリックして、カラー ピッカーを開きます。
* **R、G、B、A** を **0** に設定します。

#### <a name="setup-the-scene"></a>シーンを設定する

* [ **階層] パネル** で、[ **作成** ] をクリックし、[ **空の作成**] をクリックします。
* 新しい [作成] **オブジェクト** を右クリックし、[名前の変更] を選択します。 **OrigamiCollection** オブジェクトの名前を「」に変更します。
* [**プロジェクト] パネル** の [**ホログラム**] フォルダーから次のようにします。
  * **ステージ** を階層にドラッグして、 **OrigamiCollection** の子にします。
  * **Sphere1** を階層内にドラッグして、 **OrigamiCollection** の子にします。
  * **Sphere2** を階層内にドラッグして、 **OrigamiCollection** の子にします。
* [**階層] パネル** で **指向性ライト** オブジェクトを右クリックし、[**削除**] を選択します。
* [**ホログラム**] フォルダーから、[**階層] パネル** のルートに **ライト** をドラッグします。
* **階層** で、 **OrigamiCollection** を選択します。
* **インスペクター** で、変換位置を **0、-0.5、2.0** に設定します。
* Unity の [ **再生** ] ボタンをクリックして、ホログラムをプレビューします。
* プレビューウィンドウに Origami オブジェクトが表示されます。
* プレビューモードを停止するには、もう一度 **Play** を押します。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Unity から Visual Studio にプロジェクトをエクスポートする

* Unity で、[ **ファイル > ビルド設定**] を選択します。
* [**プラットフォーム**] ボックスの一覧で [ **Windows ストア**] を選択し、[**プラットフォームの切り替え**] をクリックします。
* **SDK** を **Universal 10** に設定し、**ビルドの種類** を **D3D** に設定します。
* **Unity C# プロジェクト** を確認します。
* シーンを追加するには、[開いている **シーンの追加** ] をクリックします。
* [ **プレーヤーの設定**] をクリックします。
* [インスペクター] パネルで、[ **Windows ストア] ロゴ** を選択します。 次に、[ **発行の設定**] を選択します。
* [ **機能** ] セクションで、 **マイク** と **SpatialPerception** 機能を選択します。
* [ビルドの設定] ウィンドウに戻り、[ **ビルド**] をクリックします。
* "App" という名前の **新しいフォルダー** を作成します。
* **アプリフォルダー** をシングルクリックします。
* **[フォルダーの選択]** をクリックします。
* Unity が完了すると、エクスプローラーウィンドウが表示されます。
* **アプリ** フォルダーを開きます。
* **Origami Visual Studio ソリューション** を開きます。
* Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **X86** に変更します。
  * デバイスのボタンの横にある矢印をクリックし、[ **HoloLens Emulator**] を選択します。
  * [ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。
  * しばらくすると、エミュレーターは Origami プロジェクトから開始されます。 [エミュレーター](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)を初めて起動するときは、エミュレーターが起動するまでに15分程度かかることがあります。 開始したら、閉じないでください。

## <a name="chapter-2---gaze"></a>第2章-宝石

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

この章では、最初に3つの方法を使用して、ホログラムと対話する方法を紹介[します。](../../../design/gaze-and-commit.md)

### <a name="objectives"></a>目標

* 世界でロックされているカーソルを使用して、宝石を視覚化します。

### <a name="instructions"></a>Instructions

* Unity プロジェクトに戻り、[ビルドの設定] ウィンドウがまだ開いている場合は閉じます。
* [**プロジェクト] パネル** で [**ホログラム**] フォルダーを選択します。
* **カーソル** オブジェクトをルートレベルの [**階層] パネル** にドラッグします。
* **カーソル** オブジェクトをダブルクリックすると、詳細が表示されます。
* [プロジェクト] パネルの [ **Scripts** ] フォルダーを右クリックします。
* [ **作成** ] サブメニューをクリックします。
* **C# スクリプト** を選択します。
* スクリプトに **WorldCursor** という名前を指定します。 注: 名前は大文字と小文字が区別されます。 .Cs 拡張子を追加する必要はありません。
* [**階層] パネル** で **カーソル** オブジェクトを選択します。
* **WorldCursor** スクリプトを [**インスペクター] パネル** にドラッグアンドドロップします。
* **WorldCursor** スクリプトをダブルクリックして、Visual Studio で開きます。
* このコードをコピーして **WorldCursor.cs** に貼り付け、 **すべて保存** します。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* **ファイル > ビルド設定** からアプリをリビルドします。
* 以前にエミュレーターに配置するために使用した Visual Studio ソリューションに戻ります。
* メッセージが表示されたら、[すべて再読み込み] を選択します。
* [ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。
* Xbox コントローラーを使用してシーンを周囲に表示します。 カーソルがオブジェクトの形状とどのように連動するかに注目してください。

## <a name="chapter-3---gestures"></a>第3章-ジェスチャ

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

この章では、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)のサポートを追加します。 ユーザーがペーパー球を選択すると、Unity の物理エンジンを使用して重力をオンにすることで、球がフォールされるようになります。

### <a name="objectives"></a>目標

* 選択ジェスチャでホログラムを制御します。

### <a name="instructions"></a>Instructions

まず、Select ジェスチャを検出できるスクリプトを作成します。

* **Scripts** フォルダーで、 **GazeGestureManager** という名前のスクリプトを作成します。
* **GazeGestureManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。
* Visual Studio で **GazeGestureManager** スクリプトを開き、次のコードを追加します。

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Scripts フォルダーに、今度は **SphereCommands** という名前の別のスクリプトを作成します。
* [階層] ビューで [ **OrigamiCollection** ] オブジェクトを展開します。
* **SphereCommands** スクリプトを、[階層] パネルの [ **Sphere1** ] オブジェクトにドラッグします。
* **SphereCommands** スクリプトを、[階層] パネルの [ **Sphere2** ] オブジェクトにドラッグします。
* 編集するために Visual Studio でスクリプトを開き、既定のコードを次のコードに置き換えます。

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。
* シーンを見て、球体の1つを中心にします。
* Xbox コントローラーの **A** ボタンを押すか、space キーを押して選択ジェスチャをシミュレートします。

## <a name="chapter-4---voice"></a>第4章-音声

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

この章では、次の2つの [音声コマンド](../../../design/voice-input.md)のサポートを追加します。 "リセット world" は、ドロップされた球体を元の場所に返し、"ドロップ球" を使用して球をフォールします。

### <a name="objectives"></a>目標

* 常にバックグラウンドで待機する音声コマンドを追加します。
* 音声コマンドに反応するホログラムを作成します。

### <a name="instructions"></a>Instructions

* **Scripts** フォルダーで、 **SpeechManager** という名前のスクリプトを作成します。
* **SpeechManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。
* Visual Studio で **SpeechManager** スクリプトを開きます。
* このコードをコピーして **SpeechManager.cs** に貼り付け、 **すべてを保存** します。

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Visual Studio で **SphereCommands** スクリプトを開きます。
* 次のようにスクリプトを更新します。

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。
* エミュレーターは PC のマイクをサポートし、音声に応答します。つまり、カーソルが球体の1つになるようにビューを調整し、"ドロップ球" と言います。
* "**世界のリセット**" と言うと、最初の位置に戻ります。

## <a name="chapter-5---spatial-sound"></a>第5章-空間サウンド

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

この章では、アプリに音楽を追加し、特定のアクションに対してサウンド効果をトリガーします。 [空間サウンド](../../../design/spatial-sound.md)を使用して、3d 空間内の特定の位置にサウンドを与えます。

### <a name="objectives"></a>目標

* 世界中のホログラムを聞くことができます。

### <a name="instructions"></a>Instructions

* Unity で、上部のメニューから [ **> プロジェクトの設定を編集** します] [オーディオ] > 選択します。
* **Spatializer プラグイン** 設定を探し、[ **MS HRTF Spatializer**] を選択します。
* [ **ホログラム** ] フォルダーから、[ **アンビエント** ] オブジェクトを [階層] パネルの **OrigamiCollection** オブジェクトにドラッグします。
* [ **OrigamiCollection** ] を選択し、 **オーディオソース** コンポーネントを検索します。 次のプロパティを変更します。
  * **Spatialize** プロパティを確認します。
  * スリープ状態 **になって** いることを確認します。
  * スライダーを右にドラッグして、 **空間 Blend** を **3d** に変更します。
  * **Loop** プロパティを確認します。
  * [ **3D サウンド設定**] を展開し、**ドップラーレベル** に「 **0.1** 」と入力します。
  * **ボリュームのロール** アウトを **対数ロールオフ** に設定します。
  * **最大距離** を **20** に設定します。
* **Scripts** フォルダーで、 **SphereSounds** という名前のスクリプトを作成します。
* **SphereSounds** を階層内の **Sphere1** オブジェクトと **Sphere2** オブジェクトにドラッグします。
* Visual Studio で **SphereSounds** を開き、次のコードを更新して **すべてを保存** します。

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* スクリプトを保存し、Unity に戻ります。
* アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。
* すべての効果を取得するための磨耗のヘッドホンと、より近くに移動し、サウンドが変化することを確認します。

## <a name="chapter-6---spatial-mapping"></a>Chapter 6-空間マッピング

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

ここでは、 [空間マッピング](../../../design/spatial-mapping.md) を使用して、ゲームボードを現実世界の実際のオブジェクトに配置します。

### <a name="objectives"></a>目標

* 実際の世界を仮想環境に移します。
* 自分にとって最も重要な場所にホログラムを配置します。

### <a name="instructions"></a>Instructions

* [プロジェクト] パネルの [ **ホログラム** ] フォルダーをクリックします。
* **空間マッピング** 資産を **階層** のルートにドラッグします。
* 階層内の **空間マッピング** オブジェクトをクリックします。
* [ **インスペクター] パネル** で、次のプロパティを変更します。
  * [ **ビジュアルメッシュの描画** ] チェックボックスをオンにします。
  * [ **素材の描画** ] を見つけ、右側にある円をクリックします。 上部にある検索フィールドに「**ワイヤーフレーム**」と入力します。 結果をクリックし、ウィンドウを閉じます。
* アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。
* アプリを実行すると、前にスキャンした実際の生活室のメッシュがワイヤーフレームでレンダリングされます。
* ローリング球がステージとフロアにどのように分かれているかを見てください。

ここでは、OrigamiCollection を新しい場所に移動する方法について説明します。

* **Scripts** フォルダーで、 **TapToPlaceParent** という名前のスクリプトを作成します。
* **階層** で、 **OrigamiCollection** を展開し、[**ステージ**] オブジェクトを選択します。
* **TapToPlaceParent** スクリプトを Stage オブジェクトにドラッグします。
* Visual Studio で **TapToPlaceParent** スクリプトを開き、次のように更新します。

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* アプリをエクスポート、ビルド、デプロイします。
* これで、特定の場所にゲームを配置できるようになりました。これを行うには、選択ジェスチャ (**a** または space キー) を使用してから新しい場所に移動し、もう一度 select ジェスチャを使用します。

## <a name="the-end"></a>最後です

これがこのチュートリアルの終わりです。

学習した内容は次のとおりです。

* Unity で holographic アプリを作成する方法。
* 見つめ、ジェスチャ、音声、サウンド、および空間マッピングを使用する方法。
* Visual Studio を使用してアプリをビルドしてデプロイする方法。

これで、独自の holographic アプリの作成を開始する準備ができました。

## <a name="see-also"></a>関連項目

* [MR の基本 101:デバイスを使用した完全なプロジェクト](holograms-101.md)
* [視線入力](../../../design/gaze-and-commit.md)
* [頭の視線入力とコミット](../../../design/gaze-and-commit.md)
* [音声入力](../../../design/voice-input.md)
* [立体音響](../../../design/spatial-sound.md)
* [空間マッピング](../../../design/spatial-mapping.md)