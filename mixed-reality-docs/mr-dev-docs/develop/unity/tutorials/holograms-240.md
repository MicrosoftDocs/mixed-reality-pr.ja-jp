---
title: MR 共有 240-複数の HoloLens デバイス
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ホログラムの共有の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、共有、ネットワーク、academy、チュートリアル
ms.openlocfilehash: 886b8b3ef449dc2872358fffd67b6af4c661de0e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690767"
---
# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 共有 240:複数の HoloLens デバイス

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。

ホログラムは、領域内での移動によって、世界中に残されています。 HoloLens は、さまざまな [座標](../../../design/coordinate-systems.md) 系を使用して、オブジェクトの位置と向きを追跡することで、ホログラムを保持します。 これらの座標系をデバイス間で共有すると、共有された holographic 世界に参加するための共有エクスペリエンスを作成できます。

このチュートリアルでは、次のことを行います。

* 共有エクスペリエンスのためにネットワークをセットアップします。
* HoloLens デバイス間でホログラムを共有します。
* 共有 holographic 世界の他のメンバーを発見します。
* 他のプレーヤーをターゲットにして projectiles を起動できる、共有のインタラクティブなエクスペリエンスを作成しましょう。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 共有 240:複数の HoloLens デバイス</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>前提条件

* インターネットアクセスを使用して適切な [ツールがインストール](../../../develop/install-the-tools.md) されている WINDOWS 10 PC。
* [開発用に構成された](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)少なくとも2つの HoloLens デバイス。

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) をダウンロードします。 Unity 2017.2 以降が必要です。
  * 引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)をご利用ください。
  * 引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)をご利用ください。
  * 引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)をご利用ください。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。 フォルダー名を **Sharedholograms** として保持します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)ます。

## <a name="chapter-1---holo-world"></a>Chapter 1-Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。

### <a name="objectives"></a>目標

* Unity をセットアップして、holographic アプリを開発します。
* ホログラムをご覧ください。

### <a name="instructions"></a>Instructions

* Unity を起動します。
* **[Open (開く)]** を選択します。
* 以前に unarchived した **Sharedholograms** フォルダーとして場所を入力します。
* [ **プロジェクト名** ] を選択し、[ **フォルダーの選択** ] をクリックします。
* **階層** で、 **メインカメラ** を右クリックし、[ **削除** ] を選択します。
* **HoloToolkit-240/Prefabs/カメラ** フォルダーで、 **メインカメラ** の事前 fab を見つけます。
* **メインカメラ** を **階層** にドラッグアンドドロップします。
* **階層** で、[ **作成** ] をクリックし、[ **空の作成** ] をクリックします。
* 新しい [作成] **オブジェクト** を右クリックし、[ **名前の変更** ] を選択します。
* **HologramCollection** オブジェクトの名前を「」に変更します。
* **階層** 内の **HologramCollection** オブジェクトを選択します。
* **インスペクター** で、 **変換位置** を **X: 0、Y:-0.25、Z: 2** のように設定します。
* [ **プロジェクト] パネル** の [ **ホログラム** ] フォルダーで、 **EnergyHub** 資産を見つけます。
* [ **プロジェクト] パネル** から、 **EnergyHub** オブジェクトを **HologramCollection の子** として **階層** にドラッグアンドドロップします。
* [ **ファイル] > 選択してシーンを保存...**
* シーンに **Sharedholograms** という名前を付け、[ **保存** ] をクリックします。
* Unity の [ **再生** ] ボタンをクリックして、ホログラムをプレビューします。
* プレビューモードを停止するには、もう一度 **Play** を押します。

**Unity から Visual Studio にプロジェクトをエクスポートする**

* Unity で、[ **ファイル > ビルド設定** ] を選択します。
* シーンを追加するには、[開いている **シーンの追加** ] をクリックします。
* [ **プラットフォーム** ] ボックスの一覧の [ **ユニバーサル Windows プラットフォーム** ] を選択し、[ **プラットフォームの切り替え** ] をクリックします。
* **SDK** を **Universal 10** に設定します。
* **ターゲットデバイス** を **HoloLens** に設定し、 **UWP ビルドの種類** を **D3D** に設定します。
* **Unity C# プロジェクト** を確認します。
* [ **ビルド** ] をクリックします。
* 表示された [エクスプローラー] ウィンドウで、"App" という名前の **新しいフォルダー** を作成します。
* **アプリ** フォルダーをシングルクリックします。
* **[フォルダーの選択]** をクリックします。
* Unity が完了すると、エクスプローラーウィンドウが表示されます。
* **アプリ** フォルダーを開きます。
* **Sharedholograms** を開いて、Visual Studio を起動します。
* Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **X86** に変更します。
* [ローカルコンピューター] の横にあるドロップダウン矢印をクリックし、[ **リモートデバイス** ] を選択します。
    * **アドレス** を HoloLens の名前または IP アドレスに設定します。 デバイスの IP アドレスがわからない場合は、[設定] の [ **ネットワーク & Internet > 詳細オプション >** 確認するか、cortana **に "Cortana さん、どのような IP アドレスがあるか" を** 確認してください。
    * [ **認証モード** ( **ユニバーサル** ) に設定したままにします。
    * [ **選択] を** クリック
* [デバッグ] をクリックして [ **デバッグなしで開始** ] を >、Ctrl キーを押し **ながら F5** キーを押します。 初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。
* HoloLens に配置し、EnergyHub ホログラムを見つけます。

## <a name="chapter-2---interaction"></a>Chapter 2-相互作用

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

この章では、ホログラムを操作します。 最初に、 [見つめ](../../../design/gaze-and-commit.md)を視覚化するカーソルを追加します。 次に、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures) を追加し、手を使用してホログラムをスペースに配置します。

### <a name="objectives"></a>目標

* 行方向の入力を使用してカーソルを制御します。
* ジェスチャ入力を使用して、ホログラムを操作します。

### <a name="instructions"></a>Instructions

**視線入力**

* [ **階層] パネル** で、 **HologramCollection** オブジェクトを選択します。
* [ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。
* メニューの [検索] ボックスに「と **入力してください」** と入力します。 検索結果を選択します。
* **HoloToolkit-Sharing-240\Prefabs\Input** フォルダーで、 **カーソル** アセットを見つけます。
* **カーソル** アセットを **階層** にドラッグアンドドロップします。

**ジェスチャ**

* [ **階層] パネル** で、 **HologramCollection** オブジェクトを選択します。
* [ **コンポーネントの追加** ] をクリックし、検索フィールドに「 **ジェスチャマネージャー** 」と入力します。 検索結果を選択します。
* [ **階層] パネル** で、[ **HologramCollection** ] を展開します。
* 子 **EnergyHub** オブジェクトを選択します。
* [ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。
* メニューで、検索ボックスの **ホログラムの配置** を入力します。 検索結果を選択します。
* [ **ファイル > [シーンの保存** ] を選択してシーンを保存します。

**デプロイと活用**

* 前の章の指示に従って、HoloLens にビルドしてデプロイします。
* HoloLens でアプリが起動したら、頭を動かして、EnergyHub がどのようになっているかをご確認ください。
* ホログラムを見つめたときにカーソルがどのように表示されるかに注目してください。また、ホログラムで見られない場合はポイントライトに変わります。
* エアタップを実行して、ホログラムを配置します。 この時点で、このプロジェクトでは、ホログラムを1回だけ配置できます (再デプロイしてもう一度試すことができます)。

## <a name="chapter-3---shared-coordinates"></a>第3章-共有座標

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

ホログラムを見て操作するのは楽しい作業ですが、さらに詳しく見ていきましょう。 最初の共有エクスペリエンスを設定します。すべてのユーザーが一緒に見ることができます。

### <a name="objectives"></a>目標

* 共有エクスペリエンスのためにネットワークをセットアップします。
* 共通の参照ポイントを確立します。
* デバイス間で座標系を共有します。
* 全員が同じホログラムを見ることがあります。

>[!NOTE]
>アプリが共有サーバーに接続するには、 **Internetclientserver** と **PrivateNetworkClientServer** の機能を宣言する必要があります。 これは、既にホログラム240に含まれていますが、独自のプロジェクトでは考慮しておいてください。

>1. Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。
>2. [Windows ストア] タブをクリックします。
>3. [発行の設定 > 機能] セクションで、 **Internetclientserver** の機能と **PrivateNetworkClientServer** 機能を確認します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト] パネル** で、 **HoloToolkit-Sharing-240\Prefabs\Sharing** フォルダーに移動します。
* **共有** prefab を [ **階層] パネル** にドラッグアンドドロップします。

次に、共有サービスを起動する必要があります。 この手順を実行する必要があるのは、共有エクスペリエンス内の **1 台の PC** だけです。

* Unity で、上部のメニューの [ **HoloToolkit-240] メニュー** を選択します。
* ドロップダウンリストで [ **共有サービスの起動** ] 項目を選択します。
* [ **プライベートネットワーク** ] オプションをオンにし、[ファイアウォールプロンプトが表示されたら **アクセスを許可** する] をクリックします。
* 共有サービスコンソールウィンドウに表示されている IPv4 アドレスをメモしておきます。 これは、サービスが実行されているコンピューターと同じ IP です。

共有エクスペリエンスに参加するすべての **pc** で、残りの手順に従います。

* **階層** で、 **共有** オブジェクトを選択します。
* **インスペクター** の [ **共有ステージ** ] コンポーネントで、 **サーバーアドレス** を ' localhost ' から SharingService.exe を実行しているコンピューターの IPv4 アドレスに変更します。
* **階層** で、 **HologramCollection** オブジェクトを選択します。
* **インスペクター** で [コンポーネントの **追加** ] ボタンをクリックします。
* 検索ボックスに、「 **Import Export Anchor Manager** 」と入力します。 検索結果を選択します。
* [ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。
* **HologramPlacement** スクリプトをダブルクリックして、Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Unity に戻り、[ **階層] パネル** で [ **HologramCollection** ] を選択します。
* [ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。
* メニューで、検索ボックスに「 **App State Manager** 」と入力します。 検索結果を選択します。

**デプロイと活用**

* HoloLens デバイス用のプロジェクトをビルドします。
* 1つの HoloLens を最初に展開するように指定します。 EnergyHub を配置する前に、アンカーがサービスにアップロードされるまで待機する必要があります (これには約30-60 秒かかることがあります)。 アップロードが完了するまで、タップジェスチャは無視されます。
* EnergyHub が配置されると、その場所がサービスにアップロードされ、他のすべての HoloLens デバイスに展開できるようになります。
* 新しい HoloLens が最初にセッションに参加したときに、そのデバイスで EnergyHub の場所が正しくない可能性があります。 ただし、アンカーと EnergyHub の場所がサービスからダウンロードされるとすぐに、EnergyHub は新しい共有の場所に移動する必要があります。 これが約30-60 秒以内に行われない場合は、アンカーを設定して、より多くの環境の手掛かりを収集するときに、元の HoloLens がどこにあったかを説明します。 その場所がまだロックされていない場合は、デバイスに再デプロイします。
* デバイスの準備が完了し、アプリを実行している場合は、EnergyHub を探します。 ホログラムの場所とテキストがどの方向に接しているかについては、すべて同意できますか。

## <a name="chapter-4---discovery"></a>Chapter 4-検出

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

全員が同じホログラムを見ることができるようになりました。 それでは、共有 holographic 世界に接続されているすべてのユーザーを見てみましょう。 この章では、同じ共有セッション内の他のすべての HoloLens デバイスの場所とローテーションについて説明します。

### <a name="objectives"></a>目標

* 共有エクスペリエンスで互いを検出します。
* プレーヤーアバターを選択して共有します。
* すべてのユーザーのヘッドの横に、プレーヤーアバターを添付します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。
* **PlayerAvatarStore** を **階層** にドラッグアンドドロップします。
* [ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。
* **AvatarSelector** スクリプトをダブルクリックして、Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* **階層** で、 **HologramCollection** オブジェクトを選択します。
* **インスペクター** で [ **コンポーネントの追加** ] をクリックします。
* 検索ボックスに、「 **Local Player Manager** 」と入力します。 検索結果を選択します。
* **階層** で、 **HologramCollection** オブジェクトを選択します。
* **インスペクター** で [ **コンポーネントの追加** ] をクリックします。
* 検索ボックスに、「 **リモートプレーヤーマネージャー** 」と入力します。 検索結果を選択します。
* Visual Studio で **HologramPlacement** スクリプトを開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Visual Studio で **AppStateManager** スクリプトを開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**デプロイと活用**

* プロジェクトをビルドし、HoloLens デバイスにデプロイします。
* Ping 音が聞こえたら、アバター選択メニューを見つけて、エアタップジェスチャでアバターを選択します。
* ホログラムを見ていない場合、カーソルの周囲のポイントライトは、HoloLens がサービスと通信しているときに、(濃い紫の) 初期化、アンカーのダウンロード (緑)、位置データのインポート/エクスポート (黄色)、アンカーのアップロード (青) で異なる色になります。 カーソルの周囲のポイントライトが既定の色 (淡い紫) の場合は、セッション内の他のプレーヤーと対話する準備ができています。
* スペースに接続されている他のユーザーを確認します。 holographic ロボットはショルダーの上にフローティングし、頭の動きを模倣しています。

## <a name="chapter-5---placement"></a>章 5: 配置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

この章では、アンカーを実際のサーフェイスに配置できるようにします。 共有座標を使用して、共有エクスペリエンスに接続されているすべてのユーザー間の中間点にアンカーを配置します。

### <a name="objectives"></a>目標

* プレーヤーのヘッド位置に基づいて、空間マッピングメッシュにホログラムを配置します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。
* **CustomSpatialMapping** Prefab を **階層** にドラッグアンドドロップします。
* [ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。
* **AppStateManager** スクリプトをダブルクリックして、Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* [ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。
* **HologramPlacement** スクリプトをダブルクリックして、Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**デプロイと活用**

* プロジェクトをビルドし、HoloLens デバイスにデプロイします。
* アプリの準備が整ったら、サークルに EnergyHub て、すべてのユーザーの中央に表示されることを確認します。
* タップして、EnergyHub を配置します。
* 音声コマンド ' Reset Target ' を使用して EnergyHub バックアップを選択し、グループとして連携して、ホログラムを新しい場所に移動してみてください。

## <a name="chapter-6---real-world-physics"></a>第6章-実際の物理

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

この章では、現実世界の表面にバウンスするホログラムを追加します。 自分と友人の両方によって起動されたプロジェクトで、スペースを埋めることができます。

### <a name="objectives"></a>目標

* 現実世界の表面にバウンドする projectiles を起動します。
* 他のプレーヤーが見ることができるように、projectiles を共有します。

### <a name="instructions"></a>Instructions

* **階層** で、 **HologramCollection** オブジェクトを選択します。
* **インスペクター** で [ **コンポーネントの追加** ] をクリックします。
* [検索] ボックスに、「"" の種類の表示 **ツール** 」と入力します。 検索結果を選択します。

**デプロイと活用**

* HoloLens デバイスにビルドしてデプロイします。
* アプリがすべてのデバイスで実行されている場合は、エアタップを実行して、実世界のサーフェイスで航空タイルを起動します。
* 他のプレーヤーのアバターと競合している場合はどうなるかを確認してください。

## <a name="chapter-7---grand-finale"></a>第7章-グランドくくり

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

この章では、コラボレーションによってのみ検出できるポータルについて説明します。

### <a name="objectives"></a>目標

* 連携して、秘密ポータルを見つけるために十分な projectiles をアンカーで立ち上げましょう。

### <a name="instructions"></a>Instructions

* [ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。
* **HologramCollection の子** として、 **黄泉** の資産をドラッグアンドドロップします。
* **HologramCollection** を選択した状態で、 **インスペクター** の [ **コンポーネントの追加** ] ボタンをクリックします。
* メニューで、検索ボックスに「 **ExplodeTarget** 」と入力します。 検索結果を選択します。
* **HologramCollection** を選択した状態で、 **階層** から、 **EnergyHub** オブジェクトを **インスペクター** の [ **ターゲット** ] フィールドにドラッグします。
* **HologramCollection** を選択した状態で、 **階層** から、 **黄泉** のオブジェクトを **インスペクター** の [ **黄泉** ] フィールドにドラッグします。

**デプロイと活用**

* HoloLens デバイスにビルドしてデプロイします。
* アプリが起動したら、共同作業を行って、EnergyHub で projectiles を起動します。
* 黄泉の場所にいる場合は、黄泉のロボットロボットで projectiles を起動します (特別に楽しいようにロボットを3回押します)。