---
title: MR 入力 213
description: Unity、Visual Studio、およびイマーシブヘッドセットを使用したこのコーディングチュートリアルに従って、モーションコントローラーの詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、イマーシブ、motion controller、academy、チュートリアル
ms.openlocfilehash: c83fd4970e40919e146b0a4e8b4f0f516e9d0906
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685378"
---
# <a name="mr-input-213-motion-controllers"></a>MR 入力 213:モーション コントローラー

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](../mr-learning-base-01.md)が投稿されています。

混合現実世界のモーションコントローラーは、別のレベルの対話機能を追加します。 [モーションコントローラー](../design/motion-controllers.md)を使用すると、リアルタイムでの物理的な相互作用と同様に、オブジェクトをより自然な方法で直接やり取りし、アプリのエクスペリエンスの immersion と満足させるを増やすことができます。

MR 入力213では、単純な空間描画エクスペリエンスを作成することによって、モーションコントローラーの入力イベントを調査します。 このアプリでは、ユーザーはさまざまな種類のブラシや色を使用して3次元空間で塗りつぶすことができます。

## <a name="topics-covered-in-this-tutorial"></a>このチュートリアルで説明するトピック

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**コントローラーの視覚化**|**コントローラーの入力イベント**|**カスタムコントローラーと UI**|
|Unity のゲームモードとランタイムでモーションコントローラーモデルをレンダリングする方法について説明します。|さまざまな種類のボタンイベントとそのアプリケーションを理解します。|コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。|

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 213:モーション コントローラー</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>前提条件

[このページ](../develop/install-the-tools.md)の「イマーシブヘッドセットのインストールチェックリスト」を参照してください。

* このチュートリアルには[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)が必要です

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な[ファイルをダウンロード](https://github.com/Microsoft/MixedReality213/archive/master.zip)し、ファイルをデスクトップに抽出します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/MixedReality213)ます。

## <a name="unity-setup"></a>Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目標

* Windows Mixed Reality 開発用に Unity を最適化する
* Mixed Reality カメラの設定
* 環境の設定

### <a name="instructions"></a>Instructions

* Unity を起動します。
* **[Open (開く)]** を選択します。
* デスクトップに移動し、以前に unarchived した **MixedReality213** フォルダーを探します。
* **[フォルダーの選択]** をクリックします。
* Unity がプロジェクトファイルの読み込みを完了すると、Unity エディターを表示できるようになります。
* Unity で、[ **ファイル > ビルド設定** ] を選択します。

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* [ **プラットフォーム** ] ボックスの一覧の [ **ユニバーサル Windows プラットフォーム** ] を選択し、[ **プラットフォームの切り替え** ] ボタンをクリックします。
* ターゲットデバイスを **任意のデバイス** に設定する
* ビルドの種類を **D3D** に設定
* SDK を **最新のインストール済み** に設定する
* **Unity C# プロジェクト** を確認する
    * これにより、Unity プロジェクトを再構築しなくても、Visual Studio プロジェクトでスクリプトファイルを変更できます。
* [ **プレーヤーの設定** ] をクリックします。
* [ **インスペクター** ] パネルで、下にスクロールします。
* XR の設定で、[ **Virtual Reality がサポートされる** ] をオンにします。
* [Virtual Reality Sdk] で、[ **Windows Mixed reality** ] を選択します。

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* **ビルドの設定** ウィンドウを閉じます。

### <a name="project-structure"></a>プロジェクト構造

このチュートリアルでは **[、Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** を使用します。 リリースは [このページ](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)で確認できます。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**参照のための完了したシーン**

* [ **シーン** ] フォルダーの下に2つの Unity シーンが完成していることがわかります。
    * **MixedReality213** : 1 つのブラシを使用した完成したシーン
    * **MixedReality213Advanced** : 複数のブラシを使用した高度なデザインのための完成したシーン

**チュートリアルの新しいシーンの設定**

* Unity で、[ **ファイル > 新しいシーン** ] をクリックします。
* **メインカメラ** と **指向性ライト** の削除
* [ **プロジェクト] パネル** で、次の prefabs を検索し、[ **階層** ] パネルにドラッグします。
    * Assets/HoloToolkit/Input/Prefabs/ **MixedRealityCamera**
    * Assets/AppPrefabs/ **Environment**

    ![カメラと環境](images/mr213-cameraenvironment-300px.jpg)

* Mixed Reality Toolkit には、次の2つのカメラ prefabs があります。
    * **MixedRealityCamera** : カメラのみ
    * **MixedRealityCameraParent** : カメラ + テレの境界線
    * このチュートリアルでは、 **MixedRealityCamera** 機能を使用せずに、この機能を使用します。 このため、基本的なフロアを含む単純な **環境** prefab を追加し、ユーザーが接地できるようにしました。
    * **MixedRealityCameraParent** を使用した電話の詳細については、 [上級設計と locomotion](#advanced-design---teleportation-and-locomotion)に関するページを参照してください。

**スカイボックスのセットアップ**

* [ **ウィンドウ > 照明 > 設定** ] をクリックします。
* [ **スカイボックス素材] フィールド** の右側にある円をクリックします。
* 「Gray」と入力し、[ **SkyboxGray** (Assets/AppPrefabs/Support/マテリアル/SkyboxGray)] を選択します。

    ![スカイボックスの設定](images/mr123-skyboxsetting-400px.jpg)

* **スカイ** ボックスをチェックして、割り当てられている灰色のグラデーションスカイボックスを確認できるようにします

    ![スカイボックスの切り替えオプション](images/mr213-skyboxcheck-400px.jpg)

* MixedRealityCamera、Environment、および gray スカイボックスのシーンは次のようになります。

    ![MixedReality213 環境](images/mr213-environment-600px.jpg)

* [ **ファイル > をクリックしてシーンを保存** ]
* シーンを任意の名前でシーンフォルダーに **保存** する

## <a name="chapter-1---controller-visualization"></a>第1章-コントローラーの視覚化

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目標

* Unity のゲームモードと実行時にモーションコントローラーモデルをレンダリングする方法について説明します。

Windows Mixed Reality は、コントローラーを視覚化するためのアニメーションコントローラーモデルを提供します。 アプリでコントローラーを視覚化するには、いくつかの方法があります。

* 既定-変更せずに既定のコントローラーを使用する
* ハイブリッド-既定のコントローラーを使用しますが、一部の要素または UI コンポーネントのオーバーレイをカスタマイズする
* 置換-コントローラー用にカスタマイズした独自の3D モデルを使用する

この章では、これらのコントローラーのカスタマイズの例について説明します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト** ] パネルで、検索ボックスに「 **motioncontrollers** 」と入力します。 また、Assets/HoloToolkit/Input/Prefabs/で見つけることもできます。
* **Motioncontrollers** prefab を [ **階層** ] パネルにドラッグします。
* [ **階層** ] パネルで、 **motioncontrollers** prefab をクリックします。

**MotionControllers prefab**

**Motioncontrollers** prefab には、代替コントローラーモデルのスロットを提供する **Motioncontrollers ビジュアライザー** スクリプトが用意されています。 独自のカスタム3D モデル (手動または剣) を割り当て、[常に代替の左/右モデルを使用する] チェックボックスをオンにすると、既定のモデルの代わりにそれらが表示されます。 このスロットを4章で使用して、コントローラーモデルをブラシで置き換えます。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**手順**

* [ **インスペクター** ] パネルで、[ **Motionコントローラービジュアライザー** スクリプト] をダブルクリックして、Visual Studio のコードを表示します。

**Motionコントローラービジュアライザースクリプト**

**Motioncontroller ビジュアライザー** と **Motioncontroller info** クラスは、既定のコントローラーモデルにアクセス & 変更する手段を提供します。 **Motioncontroller ビジュアライザー** は、Unity の **interactionsourcedetected** イベントをサブスクライブし、検出されたときにコントローラーモデルを自動的にインスタンス化します。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

コントローラーモデルは、 [glTF 仕様](https://github.com/KhronosGroup/glTF)に従って配信されます。 この形式は、一般的な形式を提供するために作成されており、3D アセットの送信とアンパックの背後にあるプロセスが改善されています。 この場合、ユーザーの操作を可能な限りシームレスにするため、実行時にコントローラーモデルを取得して読み込む必要があります。また、ユーザーが使用しているモーションコントローラーのバージョンが保証されるわけではありません。 このコースでは、Mixed Reality Toolkit を使用して、Khronos グループの [Unitygltf プロジェクト](https://github.com/KhronosGroup/UnityGLTF)のバージョンを使用します。

コントローラーが配信されると、スクリプトは **Motioncontroller info** を使用して特定のコントローラー要素の変換を見つけることができるため、適切に配置できます。

この後の章では、これらのスクリプトを使用して、UI 要素をコントローラーにアタッチする方法について説明します。

*スクリプトによっては、#if のあるコードブロックを見つけることができます **。UNITY_EDITOR** または **UNITY_WSA** 。これらのコードブロックは、Windows に配置するときに UWP ランタイムでのみ実行されます。これは、Unity エディターと UWP アプリのランタイムで使用される Api のセットが異なるためです。*

* シーンを **保存** し、[ **再生** ] ボタンをクリックします。

ヘッドセットには、モーションコントローラーを含むシーンを表示できます。 ボタンのクリック、サムスティックの移動、およびタッチパッドのタッチの強調表示に関する詳細なアニメーションを表示できます。

![視覚エフェクトの既定値 MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第2章-UI 要素のコントローラーへのアタッチ

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目標

* モーションコントローラーの要素について説明します。
* コントローラーの特定の部分にオブジェクトをアタッチする方法について説明します。

この章では、ユーザーがいつでも簡単にアクセスして操作できるコントローラーにユーザーインターフェイス要素を追加する方法について説明します。 また、タッチパッド入力を使用して簡単なカラーピッカー UI を追加する方法についても説明します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト** ] パネルで、 **Motionコントローラー情報** スクリプトを検索します。
* 検索結果から [ **Motionコントローラー情報** スクリプト] をダブルクリックして、Visual Studio のコードを確認します。

**Motionコントローラー情報スクリプト**

最初の手順は、UI をアタッチするコントローラーの要素を選択することです。 これらの要素は、 **MotionControllerInfo.cs** の **コントローラー** で定義されています。

![MR213 Motionコントローラー要素](images/mr213-motioncontrollerelements-1000px.jpg)

* **ホーム**
* **Menu**
* **つかん**
* **スティック**
* **Select**
* **タッチパッド**
* **ポインティング** 型: この要素は、方向をポイントするコントローラーの先端を表します。

**手順**

* [ **プロジェクト** ] パネルで、[ **attachtocontroller** スクリプト] を検索します。
* 検索結果から、[ **Attachtocontroller** script] をダブルクリックして Visual Studio のコードを確認します。

**AttachToController スクリプト**

**Attachtocontroller** スクリプトを使用すると、任意のオブジェクトを、指定したコントローラーのききと要素に簡単にアタッチできます。

**Attachelementtocontroller ()** で、

* **Motionコントローラー** を使用してきき手をチェックする
* **MotionTryGetElement ()** を使用して、コントローラーの特定の要素を取得します。
* コントローラーモデルから要素の変換を取得した後、その下にあるオブジェクトを親として設定し、オブジェクトのローカル位置 & 回転を0に設定します。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

**Attachtocontroller** スクリプトを使用する最も簡単な方法は、ColorPickerWheel の場合と同様に、このスクリプトを継承することです **。** **Onattachtocontroller** 関数と **OnDetachFromController** 関数をオーバーライドするだけで、コントローラーが検出または切断されたときにセットアップ/ブレークダウンを実行できます。

**手順**

* [ **プロジェクト** ] パネルで、検索ボックスに「 **ColorPickerWheel** 」と入力します。 [Assets/AppPrefabs/] の下にも表示されます。
* **ColorPickerWheel** prefab を [ **階層** ] パネルにドラッグします。
* [ **階層** ] パネルの [ **ColorPickerWheel** prefab] をクリックします。
* [ **インスペクター** ] パネルで [ **ColorPickerWheel** Script] をダブルクリックして、Visual Studio でコードを表示します。

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel スクリプト**

**ColorPickerWheel** は **attachtocontroller** を継承するため **Handedness** 、Inspector と **要素** が **インスペクター** パネルに表示されます。 左側のコントローラーのタッチパッド要素に UI をアタッチします。

![ColorPickerWheel スクリプト](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** は、 **Onattachtocontroller** と **OnDetachFromController** をオーバーライドして入力イベントをサブスクライブします。これは、タッチパッド入力による色の選択の次の章で使用されます。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* シーンを **保存** し、[ **再生** ] ボタンをクリックします。

**オブジェクトをコントローラーにアタッチするための別の方法**

スクリプトは **attachtocontroller** から継承し、 **onattachtocontroller** をオーバーライドすることをお勧めします。 ただし、これは常に可能であるとは限りません。 別の方法として、スタンドアロンコンポーネントとして使用することもできます。 これは、スクリプトをリファクタリングせずに既存の prefab をコントローラーにアタッチする場合に便利です。 セットアップを実行する前に、クラスで IsAttached が true に設定されるのを待ちます。 これを行う最も簡単な方法は、' Start ' にコルーチンを使用することです。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第3章: タッチパッド入力の操作

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目標

* タッチパッド入力データイベントを取得する方法について説明します
* タッチパッドの軸の位置情報をアプリのエクスペリエンスに使用する方法について説明します

### <a name="instructions"></a>Instructions

* [ **階層** ] パネルで、[ **ColorPickerWheel** ] をクリックします。
* [ **インスペクター** ] パネルの [ **アニメーター** ] の下で、[ **ColorPickerWheelController** ] をダブルクリックします。
* [ **アニメーター** ] タブが開いていることを確認できます。

**Unity のアニメーションコントローラーを使用した UI の表示/非表示**

アニメーションを使用して **ColorPickerWheel** UI の表示と非表示を切り替えるには、 [Unity のアニメーションシステム](https://docs.unity3d.com/Manual/AnimationOverview.html)を使用します。 **ColorPickerWheel** の **Visible** プロパティを true または false に設定すると、アニメーショントリガーの **表示** と **非表示が切り替え** られます。 **表示** と **非表示** のパラメーターは、 **ColorPickerWheelController** animation コントローラーで定義されています。

![Unity アニメーションコントローラー](images/mr123-animationcontroller-550px.jpg)

**手順**

* [ **階層** ] パネルで [ **ColorPickerWheel** prefab] を選択します。
* [ **インスペクター** ] パネルで [ **ColorPickerWheel** script] をダブルクリックして、Visual Studio でコードを表示します。

**ColorPickerWheel スクリプト**

**ColorPickerWheel** は、タッチパッドイベントをリッスンするために、Unity の **Interactionsourceupdated** イベントをサブスクライブします。

**Interactionsourceupdated ()** では、スクリプトはまず次のことを確認します。

* は、実際にはタッチパッドイベント (obj. state. **touchpadTouched** )
* 左のコントローラー (obj. state. source. **きき手** )

両方が true の場合、タッチパッドの位置 (obj. **touchpadPosition** ) は **selectorPosition** に割り当てられます。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

**Update ()** では、 **visible** プロパティに基づいて、カラーピッカーのアニメーターコンポーネントでアニメーショントリガーの表示と非表示をトリガーします。

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

**Update ()** では、 **selectorPosition** を使用して、カラーホイールのメッシュ collider に射線をキャストします。これにより、UV 位置が返されます。 この位置を使用して、カラーホイールのテクスチャのピクセル座標と色の値を見つけることができます。 この値は、 **Selectedcolor** プロパティを使用して他のスクリプトからアクセスできます。

![カラーピッカーのホイール Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Chapter 4-コントローラーモデルのオーバーライド

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目標

* カスタム3D モデルを使用してコントローラーモデルを上書きする方法について説明します。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instructions

* [ **階層** ] パネルの [ **motioncontrollers** ] をクリックします。
* [ **代替右コントローラー** ] フィールドの右側にある円をクリックします。
* **「BrushController** 」と入力し、結果から prefab を選択します。 これは Assets/AppPrefabs/ **BrushController** にあります。
* **常に代替右モデルを使用することを確認する**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** prefab は、 **階層** パネルに含まれている必要はありません。 ただし、子コンポーネントを確認するには、次のようにします。

* [ **プロジェクト** ] パネルで、「 **BrushController** 」と入力し、[ **BrushController** prefab] を [ **階層** ] パネルにドラッグします。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

**Tip** コンポーネントは **BrushController** にあります。 この変換を使用して、描画線を開始または停止します。

* [ **階層** ] パネルから **BrushController** を削除します。
* シーンを **保存** し、[ **再生** ] ボタンをクリックします。 ブラシモデルは、右側のモーションコントローラーに置き換えられていることがわかります。

## <a name="chapter-5---painting-with-select-input"></a>Chapter 5-Select 入力による塗りつぶし

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目標

* Select button イベントを使用して、線描画を開始および停止する方法について説明します。

### <a name="instructions"></a>Instructions

* [ **プロジェクト** ] パネルで **BrushController** prefab を検索します。
* [ **インスペクター** ] パネルで [ **BrushController** Script] をダブルクリックして、Visual Studio でコードを表示します。

**BrushController スクリプト**

**BrushController** は、InteractionManager の **Interactionsource押さ** れたイベントと **InteractionSourceReleased** イベントをサブスクライブします。 **Interactionsourcepressed** れたイベントがトリガーされると、ブラシの **Draw** プロパティが true に設定されます。 **InteractionSourceReleased** イベントがトリガーされると、ブラシの **Draw** プロパティが false に設定されます。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

**描画** が true に設定されている場合、ブラシはインスタンス化された Unity **LineRenderer** 内のポイントを生成します。 この prefab への参照は、ブラシの **ストローク prefab** フィールドに保持されます。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

カラーピッカーのホイール UI で現在選択されている色を使用するには、 **BrushController** が **ColorPickerWheel** オブジェクトへの参照を持っている必要があります。 **BrushController** prefab は実行時に交換用コントローラーとしてインスタンス化されるため、シーン内のオブジェクトへの参照は実行時に設定する必要があります。 この例では、 **FindObjectOfType** を使用して **ColorPickerWheel** を検索します。

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* シーンを **保存** し、[ **再生** ] ボタンをクリックします。 右側のコントローラーの [選択] ボタンを使用して、線を描画し、塗りつぶすことができます。

## <a name="chapter-6---object-spawning-with-select-input"></a>Chapter 6-Select 入力を使用したオブジェクトの生成

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目標

* 選択ボタンと表示ボタンの入力イベントを使用する方法について説明します。
* オブジェクトをインスタンス化する方法について説明します

### <a name="instructions"></a>Instructions

* [ **プロジェクト** ] パネルの [検索] ボックスに「 **ObjectSpawner** 」と入力します。 また、Assets/AppPrefabs の下にあります。
* **ObjectSpawner** prefab を [ **階層** ] パネルにドラッグします。
* [ **階層** ] パネルの [ **ObjectSpawner** ] をクリックします。
* **ObjectSpawner** には、 **Color Source** という名前のフィールドがあります。
* [ **階層** ] パネルで、 **ColorPickerWheel** 参照をこのフィールドにドラッグします。

    ![オブジェクト Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* [ **階層** ] パネルの [ **ObjectSpawner** prefab] をクリックします。
* [ **インスペクター** ] パネルで [ **ObjectSpawner** Script] をダブルクリックして、Visual Studio でコードを表示します。

**ObjectSpawner スクリプト**

**ObjectSpawner** は、空間にプリミティブメッシュ (cube、球、シリンダ) のコピーをインスタンス化します。 **Interactionsourcepressed** れたことが検出されると、きき者と、そのイベントが **interactionsourcepresstype** または **interactionsourcepresstype** であるかどうかをチェックします。

イベントを **把握** するために、現在のメッシュの種類 (球、cube、円柱) のインデックスをインクリメントします。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

**Select** イベントの場合、 **SpawnObject ()** では、新しいオブジェクトがインスタンス化され、親ではありません。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** は、 **ColorPickerWheel** を使用して、表示オブジェクトの素材の色を設定します。 生成されたオブジェクトには、その色が保持されるように、このマテリアルのインスタンスが与えられます。

* シーンを **保存** し、[ **再生** ] ボタンをクリックします。

ボタンを使用してオブジェクトを変更し、[選択] ボタンを使用してオブジェクトを生成することができます。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>アプリをビルドし、Mixed Reality ポータルにデプロイする

* Unity で、[ **ファイル > ビルド設定** ] を選択します。
* [ **開い** ているシーンの追加] をクリックして、 **ビルドのシーン** に現在のシーンを追加します。
* [ **ビルド** ] をクリックします。
* "App" という名前の **新しいフォルダー** を作成します。
* **アプリ** フォルダーをシングルクリックします。
* **[フォルダーの選択]** をクリックします。
* Unity が完了すると、エクスプローラーウィンドウが表示されます。
* **アプリ** フォルダーを開きます。
* **YourSceneName** Visual Studio ソリューションファイルをダブルクリックします。
* Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **X64** に変更します。
* [デバイス] ボタンの横にあるドロップダウン矢印をクリックし、[ **ローカルコンピューター** ] を選択します。
* メニューで [デバッグ] **、[デバッグなしで開始** ] の順にクリックする >、Ctrl キーを押し **ながら F5** キーを押します。

これで、アプリがビルドされ、Mixed Reality ポータルにインストールされます。 これは、Mixed Reality ポータルの [スタート] メニューを使用して再度起動することができます。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>高度なデザイン-放射状レイアウトを使用したブラシツール

![MixedReality213 Main](images/mr213-main-600px.jpg)

この章では、既定のモーションコントローラーモデルをカスタムブラシツールコレクションに置き換える方法について説明します。 参考までに **、[シーン** ] フォルダーの下の完成したシーン **MixedReality213Advanced** を見つけることができます。

### <a name="instructions"></a>Instructions

* [ **プロジェクト** ] パネルの [検索] ボックスに「 **BrushSelector** 」と入力します。 また、Assets/AppPrefabs の下にあります。
* **BrushSelector** prefab を [ **階層** ] パネルにドラッグします。
* 組織の場合は、 **ブラシ** と呼ばれる空のオブジェクトを作成します。
* [ **プロジェクト** ] パネルから [ **ブラシ** ] に次の prefabs をドラッグします。
    * Assets/AppPrefabs/ **BrushFat**
    * Assets/AppPrefabs/ **BrushThin**
    * Assets/AppPrefabs/ **消しゴム**
    * Assets/AppPrefabs/ **MarkerFat**
    * Assets/AppPrefabs/ **MarkerThin**
    * Assets/AppPrefabs/ **鉛筆**

    ![ブラシ](images/mixedreality213-brushes-250px.png)

* [ **階層** ] パネルの [ **motioncontrollers** prefab] をクリックします。
* [ **インスペクター** ] パネルの [ **モーションコントローラービジュアライザー** で **常に代替モデルを使用する** ] チェックボックスをオフにします。
* [ **階層** ] パネルで、[ **BrushSelector** ] をクリックします。
* **BrushSelector** に **colorpicker** という名前のフィールドがある
* [ **階層** ] パネルで、[ **ColorPickerWheel** ] を [ **インスペクター** ] パネルの [ **colorpicker** ] フィールドにドラッグします。

    ![ColorPickerWheel をブラシセレクターに割り当てる](images/mr213-brushselector-500px.jpg)

* [ **階層** ] パネルの [ **BrushSelector** Prefab] で、 **メニュー** オブジェクトを選択します。
* [ **インスペクター** ] パネルの **lineobjectcollection** コンポーネントで、[ **オブジェクト** 配列] ドロップダウンを開きます。 6個の空のスロットが表示されます。
* [ **階層** ] パネルで、[ **ブラシ** の prefabs] の下にある各親を、任意の順序でこれらのスロットにドラッグします。 (プロジェクトフォルダー内の prefabs ではなく、シーンから prefabs をドラッグしていることを確認してください)。

![ブラシセレクター](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

**BrushSelector** は **attachtocontroller** を継承するため、[ **Inspector** ] パネルに **きき** と **要素** のオプションが表示されます。 **右** を選択し、[ポーズ] を **ポイント** して、右のコントローラーに [ブラシ] ツールを接続します。

**BrushSelector** は、次の2つのユーティリティを使用します。

* **楕円** : 楕円形に沿って空間内のポイントを生成するために使用されます。
* **Lineobjectcollection** : 任意の行クラスによって生成された点を使用してオブジェクトを分散します (例: 楕円)。 ここでは、楕円の形状に沿ってブラシを配置するために使用します。

これらのユーティリティを組み合わせて使用すると、放射状メニューを作成できます。

**LineObjectCollection スクリプト**

**Lineobjectcollection** には、その行に沿って分布するオブジェクトのサイズ、位置、および回転を制御します。 これは、ブラシセレクターのような放射状メニューを作成する場合に便利です。 中心が選択された位置に近づいたときに、何もスケールアップしないブラシの外観を作成するために、 **objectscale** 曲線は中央にピークし、端に tapers ます。

**BrushSelector スクリプト**

**BrushSelector** の場合、手続き型アニメーションを使用することを選択しました。 最初に、ブラシモデルは **Lineobjectcollection** スクリプトによって楕円で配分されます。 次に、各ブラシは、選択内容に基づいて変化する **DisplayMode** 値に基づいて、ユーザー側での位置を維持する役割を担います。 ユーザーがブラシを選択したときにブラシの位置の切り替えが中断される可能性が高いため、手続き型の方法を選択しました。 Mecanim アニメーションは中断を適切に処理できますが、単純な Lerp 操作よりも複雑になる傾向があります。

**BrushSelector** は、両方の組み合わせを使用します。 タッチパッドの入力が検出されると、ブラシのオプションが表示され、放射状メニューに沿ってスケールアップされます。 タイムアウト期間が経過すると (ユーザーが選択を行ったことを示す)、ブラシのオプションが再度スケールダウンされ、選択したブラシだけが残ります。

**タッチパッド入力の視覚化**

コントローラーモデルが完全に置き換えられている場合でも、元のモデル入力に入力を表示すると便利な場合があります。 これは、実際にユーザーの操作をグラウンドにするのに役立ちます。 **BrushSelector** の場合、入力を受け取ったときにタッチパッドを短時間で表示するように選択しました。 これを行うには、コントローラーからタッチパッド要素を取得し、そのマテリアルをカスタムマテリアルに置き換えて、タッチパッド入力を最後に受信したときに基づいてそのマテリアルの色にグラデーションを適用します。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**タッチパッド入力によるブラシツールの選択**

ブラシセレクターがタッチパッドの押された入力を検出すると、入力の位置を調べて、左または右にあるかどうかを確認します。

**SelectPressedAmount を使用したストロークの太さ**

**Interactionsourcepresstype ()** 内の **Select** イベントの代わりに、 **selectPressedAmount** を使用して、押された量のアナログ値を取得できます。 この値は、 **Interactionsourceupdated ()** で取得できます。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**消しゴムスクリプト**

**消しゴム** は、基本 **ブラシ** の **drawovertime ()** 関数をオーバーライドする特殊な種類のブラシです。 描画が true の場合、消しゴムは、そのチップが既存のブラシストロークと交差しているかどうかを確認します。 存在する場合は、圧縮されて削除されるようにキューに追加されます。

## <a name="advanced-design---teleportation-and-locomotion"></a>高度な設計-電話と locomotion

ユーザーがサムスティックを使用して、ユーザーによるシーンの移動を許可する場合は、 **MixedRealityCamera** ではなく **MixedRealityCameraParent** を使用します。 **Inputmanager** と **defaultcursor** も追加する必要があります。 **MixedRealityCameraParent** には既に **Motioncontrollers** と **境界** が子コンポーネントとして含まれているため、既存の **motioncontrollers** と **環境** prefab を削除する必要があります。

### <a name="instructions"></a>Instructions

* [ **階層** ] パネルで、 **MixedRealityCamera** 、 **Environment** 、 **motioncontrollers** を削除します。
* [ **プロジェクト] パネル** で、次の prefabs を検索し、[ **階層** ] パネルにドラッグします。
    * Assets/AppPrefabs/Input/Prefabs/ **MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/ **Inputmanager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/ **Defaultcursor**

    ![Mixed Reality カメラの親](images/mr213-cameraparent-300px.png)

* [ **階層** ] パネルで、[ **入力マネージャー** ] をクリックします。
* [ **インスペクター** ] パネルで、 **単純な単一ポインターセレクター** セクションまで下にスクロールします。
* [ **階層** ] パネルで、[ **Defaultcursor** ] を **カーソル** フィールドにドラッグします。

    ![DefaultCursor の割り当て](images/mr213-defaultcursor-500px.png)

* シーンを **保存** し、[ **再生** ] ボタンをクリックします。 サムスティックを使用して、左/右に回転したり、テレポートしたりすることができます。

## <a name="the-end"></a>最後です

これがこのチュートリアルの終わりです。 学習した内容は次のとおりです。

* Unity のゲームモードとランタイムでモーションコントローラーモデルを操作する方法について説明します。
* さまざまな種類のボタンイベントとそのアプリケーションを使用する方法。
* コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。

これで、モーションコントローラーで独自のイマーシブエクスペリエンスを作成する準備が整いました。

## <a name="completed-scenes"></a>完成したシーン

* Unity の [ **プロジェクト** ] パネルで、[ **シーン** ] フォルダーをクリックします。
* Unity シーン **MixedReality213** と **MixedReality213Advanced** が2つ見つかります。
    * **MixedReality213** : 1 つのブラシを使用した完成したシーン
    * **MixedReality213Advanced** : 複数のブラシを持つ完成したシーンを選択ボタンの押す回数の例

## <a name="see-also"></a>関連項目

* [MR 入力213プロジェクトファイル](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality Toolkit-モーションコントローラーテストシーン](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit-グラブ機構](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [モーションコントローラーの開発ガイドライン](../design/motion-controllers.md)
