---
title: Unity の HP リバーブ G2 コントローラー
description: SteamVR および Windows Mixed Reality で HP リバーブ G2 コントローラーを使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, リバーブ, リバーブ G2, HP リバーブ G2, mixed reality, 開発, モーションコントローラー, ユーザー入力, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 機能, ホログラム, ゲーム開発
ms.openlocfilehash: 17f373a3d94740bf103821b85ee5d6fe4dbaa11f
ms.sourcegitcommit: 8b16945d6a551f174a65fa3980ba392682ca45d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886255"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity の HP リバーブ G2 コントローラー

HP Motion controller は、まったく新しい種類の Windows Mixed Reality コントローラーであり、使用可能な入力のセットが少し異なり、すべて同じ追跡テクノロジです。 

* タッチパッドは、A と B の右側のコントローラーの2つのボタンで置き換えられました。左コントローラーの場合は X と Y になります。 
* つかみは、押された状態と押されていないボタンの代わりに、0.0 ~ 1.0 の範囲の値のストリームを公開するトリガーになりました。 

新しい入力には既存の Windows と Unity の Api からアクセスできないため、専用の **MixedReality** UPM パッケージが必要です。 

> [!IMPORTANT]
> **このパッケージのクラスは、既存の Windows と Unity の Api を置き換えるのではなく、それを補完します。** 従来の Windows Mixed Reality コントローラーと HP Motion Controller の両方で一般公開されている機能は、既存の Api を使用して同じコードパスを介してアクセスできます。 新しい入力のみで、追加の MixedReality パッケージを使用する必要があります。 

## <a name="hp-motion-controller-overview"></a>HP Motion Controller の概要

*MixedReality* は、モーションコントローラーを表します。 各 *Motioncontroller* インスタンスには *XR があります。付い.入力します。 InteractionSource* ピアは、きき、ベンダ ID、製品 id、およびバージョンを使用して相関させることができます。 

MotionController のインスタンスを取得するには、 *Motioncontroller ウォッチャー* を作成し、そのイベントをサブスクライブします。 *interactionmanager* イベントを使用して新しい *interactionmanager* インスタンスを検出するのと同様です。 MotionController のメソッドとプロパティは、コントローラーでサポートされている入力 (ボタン、トリガー、2D 軸、およびサムスティックを含む) を記述します。 MotionController クラスは、 *Motioncontroller 読み取り* クラスを介して入力状態にアクセスするためのメソッドも公開します。 Motioncontroller 読み取りクラスは、特定の時点でのコントローラーの状態のスナップショットを表します。 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Unity パッケージマネージャーを使用した MixedReality のインストール 

Unity パッケージマネージャーでは、 [マニフェストファイル](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (で manifest.js) を使用して、インストールするパッケージと、インストール先として使用できるレジストリ (サーバー) を決定します。 MixedReality パッケージを使用するには、その前に Mixed Reality コンポーネントサーバーを登録する必要があります。

### <a name="registering-the-mixed-reality-component-server"></a>Mixed Reality コンポーネントサーバーを登録しています 

Mixed Reality 入力パッケージを使用するプロジェクトごとに、(Packages フォルダー内の) ファイルの manifest.jsには、Mixed Reality スコープレジストリが追加されている必要があります。 Mixed Reality をサポートするために manifest.jsを適切に変更するには、次のようにします。 
    1. <projectRoot>Visual Studio Code などのテキストエディターで、/パッケージ/manifest.jsを開きます。 
    2. マニフェストファイルの先頭にある [スコープされたレジストリ] セクションに Mixed Reality サーバーを追加し、ファイルを保存します。 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a>MixedReality パッケージの追加 

<projectRoot>Mixedreality パッケージを追加してファイルを保存するには、テキストエディターで、ファイルの [依存関係] manifest.jsセクションを変更します。 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>MixedReality の使用 

### <a name="input-values"></a>入力値

MotionController は、次の2種類の入力を公開できます。 

* ボタンとトリガーの状態は、それらがどれだけ押されているかを示す、0.0 ~ 1.0 の一意の浮動小数点値で表されます。
    * ボタンが返すことができるのは、0.0 (押されていない場合) または 1.0 (押されている場合) のみです。トリガーは、0.0 (完全に解放) から 1.0 (完全に押された状態) まで連続する値を返すことができます。 
* サムスティック状態は、X および Y コンポーネントが-1.0 ~ 1.0 の範囲内にある Vector2.x によって表されます。 

*Motioncontroller. GetPressableInputs ()* を使用すると、押された値 (ボタンとトリガー) を返す入力の一覧を返すか、または *Motioncontroller. GetXYInputs ()* メソッドを使用して2軸の値を返す入力の一覧を返すことができます。 

Motioncontroller 読み取りインスタンスは、特定の時点のコントローラーの状態を表します。 

* *GetPressedValue ()* は、ボタンまたはトリガーの状態を取得します。 
* *GetXYValue ()* は、サムスティックの状態を取得します。 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>MotionController インスタンスのコレクションとその状態を維持するキャッシュの作成 

まず、MotionController ウォッチャーをインスタンス化し、 *Motioncontroller が追加さ* れ、Motioncontroller が *削除* されたイベントのハンドラーを登録して、使用可能な motioncontroller インスタンスのキャッシュを保持します。 このキャッシュは、次のコードに示すように、このオブジェクトに接続されているモノの動作である必要があります。

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>ポーリングによる新しい入力の読み取り 

*TryGetReadingAtTime* を使用し *て、各* 既知のコントローラーの現在の状態を読み取ることができます。 タイムスタンプパラメーターとして *DateTime. Now* を渡して、コントローラーの最新の状態が読み取られるようにします。 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

コントローラーのきき方を使用して、コントローラーの現在の入力値を取得できます。 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

たとえば、InteractionSource のアナログのつかみの値を読み取るには、次のようにします。 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>新しい入力からのイベントの生成 

フレームごとに1つのコントローラーの状態をポーリングするのではなく、すべての状態の変更をイベントとして処理することができます。これにより、フレームよりも短い最短のアクションを処理できます。 このアプローチを機能させるには、最後のフレームからコントローラーによって発行されたすべての状態をモーションコントローラーのキャッシュで処理する必要があります。これは、MotionController から取得された最後の Motioncontroller 読み取りのタイムスタンプを格納し、 *motioncontroller. TryGetReadingAfterTime ()* を呼び出すことによって実行できます。 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

キャッシュの内部クラスを更新したので、次のように、モノ Behavior クラスは2つのイベント (押された状態と解放済み) を公開し、Update () メソッドからそれらのイベントを発生させることができます。 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

上記のコード例の構造により、イベントの登録がはるかに読みやすくなります。 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>関連項目

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->