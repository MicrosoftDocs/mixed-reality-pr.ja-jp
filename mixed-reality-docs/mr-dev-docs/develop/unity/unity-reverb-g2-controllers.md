---
title: Unity の HP リバーブ G2 コントローラー
description: SteamVR および Windows Mixed Reality Unity アプリケーションで、新しい HP リバーブ G2 コントローラーをセットアップして使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, リバーブ, リバーブ G2, HP リバーブ G2, mixed reality, 開発, モーションコントローラー, ユーザー入力, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 機能, ホログラム, ゲーム開発
ms.openlocfilehash: 26435ef57c9baf59b1008fb4750aedd913a19814
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421397"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="8d219-104">Unity の HP リバーブ G2 コントローラー</span><span class="sxs-lookup"><span data-stu-id="8d219-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="8d219-105">HP Motion controller は、まったく新しい種類の Windows Mixed Reality コントローラーであり、使用可能な入力のセットが少し異なり、すべて同じ追跡テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="8d219-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="8d219-106">タッチパッドは、A と B の右側のコントローラーの2つのボタンで置き換えられました。左コントローラーの場合は X と Y になります。</span><span class="sxs-lookup"><span data-stu-id="8d219-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="8d219-107">つかみは、押された状態と押されていないボタンの代わりに、0.0 ~ 1.0 の範囲の値のストリームを公開するトリガーになりました。</span><span class="sxs-lookup"><span data-stu-id="8d219-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="8d219-108">新しい入力には既存の Windows と Unity の Api からアクセスできないため、専用の **MixedReality** UPM パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d219-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="8d219-109">**このパッケージのクラスは、既存の Windows と Unity の Api を置き換えるのではなく、それを補完します。**</span><span class="sxs-lookup"><span data-stu-id="8d219-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="8d219-110">従来の Windows Mixed Reality コントローラーと HP Motion Controller の両方で一般公開されている機能は、既存の Api を使用して同じコードパスを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8d219-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="8d219-111">新しい入力のみで、追加の MixedReality パッケージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d219-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="8d219-112">HP Motion Controller の概要</span><span class="sxs-lookup"><span data-stu-id="8d219-112">HP Motion Controller overview</span></span>

<span data-ttu-id="8d219-113">*MixedReality* は、モーションコントローラーを表します。</span><span class="sxs-lookup"><span data-stu-id="8d219-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="8d219-114">各 *Motioncontroller* インスタンスには *XR があります。付い.入力します。 InteractionSource* ピアは、きき、ベンダ ID、製品 id、およびバージョンを使用して相関させることができます。</span><span class="sxs-lookup"><span data-stu-id="8d219-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="8d219-115">MotionController のインスタンスを取得するには、 *Motioncontroller ウォッチャー* を作成し、そのイベントをサブスクライブします。 *interactionmanager* イベントを使用して新しい *interactionmanager* インスタンスを検出するのと同様です。</span><span class="sxs-lookup"><span data-stu-id="8d219-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="8d219-116">MotionController のメソッドとプロパティは、コントローラーでサポートされている入力 (ボタン、トリガー、2D 軸、およびサムスティックを含む) を記述します。</span><span class="sxs-lookup"><span data-stu-id="8d219-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="8d219-117">MotionController クラスは、 *Motioncontroller 読み取り* クラスを介して入力状態にアクセスするためのメソッドも公開します。</span><span class="sxs-lookup"><span data-stu-id="8d219-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="8d219-118">Motioncontroller 読み取りクラスは、特定の時点でのコントローラーの状態のスナップショットを表します。</span><span class="sxs-lookup"><span data-stu-id="8d219-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="8d219-119">Mixed Reality 機能ツールを使用した MixedReality のインストール</span><span class="sxs-lookup"><span data-stu-id="8d219-119">Installing Microsoft.MixedReality.Input with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="8d219-120">新しい Mixed Reality 機能ツールアプリケーションを使用して MixedReality プラグインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8d219-120">Install the Microsoft.MixedReality.Input plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="8d219-121">[インストールと使用に関する指示](welcome-to-mr-feature-tool.md)に従って、Mixed reality Toolkit カテゴリで **mixed reality 入力** パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="8d219-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Input** package in the Mixed Reality Toolkit category:</span></span>

![Mixed reality 入力が強調表示されている mixed Reality 機能ツールパッケージウィンドウ](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="8d219-123">MixedReality の使用</span><span class="sxs-lookup"><span data-stu-id="8d219-123">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="8d219-124">入力値</span><span class="sxs-lookup"><span data-stu-id="8d219-124">Input values</span></span>

<span data-ttu-id="8d219-125">MotionController は、次の2種類の入力を公開できます。</span><span class="sxs-lookup"><span data-stu-id="8d219-125">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="8d219-126">ボタンとトリガーの状態は、それらがどれだけ押されているかを示す、0.0 ~ 1.0 の一意の浮動小数点値で表されます。</span><span class="sxs-lookup"><span data-stu-id="8d219-126">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="8d219-127">ボタンが返すことができるのは、0.0 (押されていない場合) または 1.0 (押されている場合) のみです。トリガーは、0.0 (完全に解放) から 1.0 (完全に押された状態) まで連続する値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d219-127">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="8d219-128">サムスティック状態は、X および Y コンポーネントが-1.0 ~ 1.0 の範囲内にある Vector2.x によって表されます。</span><span class="sxs-lookup"><span data-stu-id="8d219-128">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="8d219-129">*Motioncontroller. GetPressableInputs ()* を使用すると、押された値 (ボタンとトリガー) を返す入力の一覧を返すか、または *Motioncontroller. GetXYInputs ()* メソッドを使用して2軸の値を返す入力の一覧を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d219-129">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="8d219-130">Motioncontroller 読み取りインスタンスは、特定の時点のコントローラーの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="8d219-130">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="8d219-131">*GetPressedValue ()* は、ボタンまたはトリガーの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d219-131">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="8d219-132">*GetXYValue ()* は、サムスティックの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d219-132">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="8d219-133">MotionController インスタンスのコレクションとその状態を維持するキャッシュの作成</span><span class="sxs-lookup"><span data-stu-id="8d219-133">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="8d219-134">まず、MotionController ウォッチャーをインスタンス化し、 *Motioncontroller が追加さ* れ、Motioncontroller が *削除* されたイベントのハンドラーを登録して、使用可能な motioncontroller インスタンスのキャッシュを保持します。</span><span class="sxs-lookup"><span data-stu-id="8d219-134">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="8d219-135">このキャッシュは、次のコードに示すように、このオブジェクトに接続されているモノの動作である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d219-135">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="8d219-136">ポーリングによる新しい入力の読み取り</span><span class="sxs-lookup"><span data-stu-id="8d219-136">Reading new inputs by polling</span></span> 

<span data-ttu-id="8d219-137">*TryGetReadingAtTime* を使用し *て、各* 既知のコントローラーの現在の状態を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8d219-137">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="8d219-138">タイムスタンプパラメーターとして *DateTime. Now* を渡して、コントローラーの最新の状態が読み取られるようにします。</span><span class="sxs-lookup"><span data-stu-id="8d219-138">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="8d219-139">コントローラーのきき方を使用して、コントローラーの現在の入力値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8d219-139">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="8d219-140">たとえば、InteractionSource のアナログのつかみの値を読み取るには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="8d219-140">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="8d219-141">新しい入力からのイベントの生成</span><span class="sxs-lookup"><span data-stu-id="8d219-141">Generating events from the new inputs</span></span> 

<span data-ttu-id="8d219-142">フレームごとに1つのコントローラーの状態をポーリングするのではなく、すべての状態の変更をイベントとして処理することができます。これにより、フレームよりも短い最短のアクションを処理できます。</span><span class="sxs-lookup"><span data-stu-id="8d219-142">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="8d219-143">このアプローチを機能させるには、最後のフレームからコントローラーによって発行されたすべての状態をモーションコントローラーのキャッシュで処理する必要があります。これは、MotionController から取得された最後の Motioncontroller 読み取りのタイムスタンプを格納し、 *motioncontroller. TryGetReadingAfterTime ()* を呼び出すことによって実行できます。</span><span class="sxs-lookup"><span data-stu-id="8d219-143">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="8d219-144">キャッシュの内部クラスを更新したので、次のように、モノ Behavior クラスは2つのイベント (押された状態と解放済み) を公開し、Update () メソッドからそれらのイベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="8d219-144">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="8d219-145">上記のコード例の構造により、イベントの登録がはるかに読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="8d219-145">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="8d219-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d219-146">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->