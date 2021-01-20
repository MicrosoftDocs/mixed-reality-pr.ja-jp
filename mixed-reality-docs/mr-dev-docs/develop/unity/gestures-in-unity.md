---
title: Unity でのジェスチャ
description: XR および共通のボタンと軸の Api を使用して手書きのジェスチャ入力を使用して、Unity での操作を実行する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: ジェスチャ, unity, 宝石, 入力, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 44c42abdd4628cacd6af334a916fb725da8bb022
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583894"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="feb58-104">Unity でのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="feb58-104">Gestures in Unity</span></span>

<span data-ttu-id="feb58-105">[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="feb58-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="feb58-106">Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="feb58-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="feb58-107">Unity には、Windows Mixed Reality の空間入力データにアクセスする主な方法が2つあります。</span><span class="sxs-lookup"><span data-stu-id="feb58-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="feb58-108">Common *input. GetButton/GetAxis* api は複数の Unity XR sdk に対して機能しますが、Windows Mixed Reality に固有の *Interactionmanager/GestureRecognizer* api は、空間入力データの完全なセットを公開します。</span><span class="sxs-lookup"><span data-stu-id="feb58-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="feb58-109">高レベル複合ジェスチャ Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="feb58-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="feb58-110">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="feb58-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="feb58-111">**型**: *GestureRecognizer*、 *GestureSettings*、 *interactionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="feb58-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="feb58-112">アプリでは、空間入力ソース、タップ、ホールド、操作、およびナビゲーションジェスチャに対する高レベルの複合ジェスチャを認識することもできます。</span><span class="sxs-lookup"><span data-stu-id="feb58-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="feb58-113">GestureRecognizer を使用して、[ハンド](../../design/gaze-and-commit.md#composite-gestures)[コントローラーとモーションコントローラー](../../design/motion-controllers.md)の両方でこれらの複合ジェスチャを認識できます。</span><span class="sxs-lookup"><span data-stu-id="feb58-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="feb58-114">GestureRecognizer の各ジェスチャイベントは、イベントの発生時に、入力とターゲットのヘッドレイを提供します。</span><span class="sxs-lookup"><span data-stu-id="feb58-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="feb58-115">一部のイベントは、コンテキスト固有の追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="feb58-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="feb58-116">ジェスチャ認識エンジンを使用してジェスチャをキャプチャするには、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="feb58-117">新しいジェスチャ認識エンジンを作成する</span><span class="sxs-lookup"><span data-stu-id="feb58-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="feb58-118">監視するジェスチャを指定する</span><span class="sxs-lookup"><span data-stu-id="feb58-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="feb58-119">これらのジェスチャのイベントをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="feb58-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="feb58-120">ジェスチャのキャプチャを開始する</span><span class="sxs-lookup"><span data-stu-id="feb58-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="feb58-121">新しいジェスチャ認識エンジンを作成する</span><span class="sxs-lookup"><span data-stu-id="feb58-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="feb58-122">*GestureRecognizer* を使用するには、 *GestureRecognizer* を作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="feb58-123">監視するジェスチャを指定する</span><span class="sxs-lookup"><span data-stu-id="feb58-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="feb58-124">*Set認識 Izableジェスチャー ()* を使用して、興味のあるジェスチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="feb58-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="feb58-125">これらのジェスチャのイベントをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="feb58-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="feb58-126">関心のあるジェスチャのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="feb58-126">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="feb58-127">ナビゲーションと操作のジェスチャは、 *GestureRecognizer* のインスタンスで相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="feb58-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="feb58-128">ジェスチャのキャプチャを開始する</span><span class="sxs-lookup"><span data-stu-id="feb58-128">Start capturing gestures</span></span>

<span data-ttu-id="feb58-129">既定では、 *GestureRecognizer* は、 *Startcapturinggestures ()* が呼び出されるまで、入力を監視しません。</span><span class="sxs-lookup"><span data-stu-id="feb58-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="feb58-130">Stopcapturinggestures () が *処理されたフレーム* の前に入力が実行された場合、 *Stopcapturinggestures ()* が呼び出された後にジェスチャイベントが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="feb58-131">*GestureRecognizer* は、ジェスチャが実際に発生した前のフレームでオンまたはオフになっていたかどうかを記憶します。そのため、このフレームのターゲット設定に基づいてジェスチャの監視を開始および停止するのは安全です。</span><span class="sxs-lookup"><span data-stu-id="feb58-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="feb58-132">ジェスチャのキャプチャを停止します</span><span class="sxs-lookup"><span data-stu-id="feb58-132">Stop capturing gestures</span></span>

<span data-ttu-id="feb58-133">ジェスチャ認識を停止するには:</span><span class="sxs-lookup"><span data-stu-id="feb58-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="feb58-134">ジェスチャ認識エンジンの削除</span><span class="sxs-lookup"><span data-stu-id="feb58-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="feb58-135">*GestureRecognizer* オブジェクトを破棄する前に、サブスクライブされたイベントのサブスクリプションを解除してください。</span><span class="sxs-lookup"><span data-stu-id="feb58-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="feb58-136">Unity でのモーションコントローラーモデルのレンダリング</span><span class="sxs-lookup"><span data-stu-id="feb58-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="feb58-137">![モーションコントローラーモデルとテレ](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="feb58-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="feb58-138">*モーションコントローラーモデルとテレ*</span><span class="sxs-lookup"><span data-stu-id="feb58-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="feb58-139">ユーザーが保持している物理コントローラーに一致するモーションコントローラーをアプリでレンダリングし、さまざまなボタンが押されていることを明確にするために、 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)で **motioncontroller prefab** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="feb58-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="feb58-140">この prefab は、システムのインストールされている motion controller ドライバーから、実行時に正しい glTF モデルを動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="feb58-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="feb58-141">これらのモデルは、エディターで手動でインポートするのではなく、動的に読み込むことが重要です。これにより、ユーザーが現在使用しているコントローラーと将来のコントローラーに対して、アプリケーションで物理的に正確な3D モデルが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="feb58-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="feb58-142">[はじめに](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)の手順に従って、Mixed Reality Toolkit をダウンロードし、Unity プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="feb58-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="feb58-143">はじめにの手順の一部としてカメラを *MixedRealityCameraParent* prefab に置き換えると、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="feb58-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="feb58-144">この事前 fab には、モーションコントローラーレンダリングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="feb58-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="feb58-145">それ以外の場合は、 *Assets/HoloToolkit/Input/Prefabs/MotionControllers* を [プロジェクト] ウィンドウからシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="feb58-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="feb58-146">この prefab は、シーン内のユーザーが携帯電話に接続しているときに、カメラを移動するために使用する親オブジェクトの子として追加します。これにより、コントローラーはユーザーと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="feb58-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="feb58-147">アプリに電話移植が含まれていない場合は、シーンのルートに prefab を追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="feb58-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="feb58-148">オブジェクトのスロー</span><span class="sxs-lookup"><span data-stu-id="feb58-148">Throwing objects</span></span>

<span data-ttu-id="feb58-149">仮想現実のオブジェクトをスローすることは、最初に考えられるよりも難しい問題です。</span><span class="sxs-lookup"><span data-stu-id="feb58-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="feb58-150">ほとんどの物理的な相互作用と同様に、ゲームでのスローは予期しない方法で動作しますが、immersion はすぐに明らかになり、壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="feb58-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="feb58-151">私たちは、物理的に正しいスロー動作を表す方法について、少し時間をかけてきました。また、お客様と共有するプラットフォームの更新によって有効になるガイドラインがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="feb58-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="feb58-152">スローを実装する方法の例については、 [こちら](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feb58-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="feb58-153">このサンプルは、次の4つのガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="feb58-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="feb58-154">**位置ではなく、コントローラーの *ベロシティ* を使用** します。</span><span class="sxs-lookup"><span data-stu-id="feb58-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="feb58-155">Windows の11月の更新プログラムでは、 [' ' 概算 ' ' 位置追跡状態](../../design/motion-controllers.md#controller-tracking-state)での動作の変更が導入されました。</span><span class="sxs-lookup"><span data-stu-id="feb58-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="feb58-156">この状態になると、高い精度を維持している限り、コントローラーに関する速度に関する情報が引き続き報告されます。</span><span class="sxs-lookup"><span data-stu-id="feb58-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="feb58-157">**コントローラーの *角速度* を組み込み** ます。</span><span class="sxs-lookup"><span data-stu-id="feb58-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="feb58-158">このロジックはすべて、上記の `throwing.cs` リンクされ `GetThrownObjectVelAngVel` たパッケージ内の静的メソッドのファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="feb58-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="feb58-159">角速度が節約であるため、スローされたオブジェクトは、スローの時点と同じ角度速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="feb58-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="feb58-160">スローされたオブジェクトの質量の中心がグリップの原因ではない可能性があるため、ユーザーの参照フレーム内のコントローラーの速度とは、ベロシティが異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="feb58-161">この方法で発生したオブジェクトのベロシティの部分は、コントローラーの原点を中心としてスローされたオブジェクトの質量の中心となる瞬間流速度です。</span><span class="sxs-lookup"><span data-stu-id="feb58-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="feb58-162">この接線速度は、コントローラーの原点と、スローされたオブジェクトの質量の中心との距離を表すベクトルを使用して、コントローラーの角速度のクロス積です。</span><span class="sxs-lookup"><span data-stu-id="feb58-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="feb58-163">スローされたオブジェクトの合計速度は、コントローラーのベロシティとこの接線速度の合計です。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="feb58-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="feb58-164">**速度を適用する *時間* に細心の注意を** 払ってください。</span><span class="sxs-lookup"><span data-stu-id="feb58-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="feb58-165">ボタンを押すと、そのイベントが Bluetooth 経由でオペレーティングシステムに対してバブルアップされるまでに最大20ミリ秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="feb58-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="feb58-166">これは、コントローラーの状態の変化をポーリングしたときに、押された状態または押されていない状態の変化をポーリングした場合に、そのコントローラーの状態が変更される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="feb58-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="feb58-167">さらに、ポーリング API によって提示されるコントローラーは、フレームが表示されるときに発生する可能性があることを反映するためにフォワード予測が行われます。これは、今後20ミリ秒を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="feb58-168">これは、保持されているオブジェクトを *レンダリング* する場合に適していますが、ユーザーがスローを解放した瞬間の軌道を計算するときに、オブジェクトを *ターゲット* にするための時間の問題が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="feb58-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="feb58-169">幸いにも、11月の更新プログラムでは、 *Interactionsourcepressed* れた、 *InteractionSourceReleased* などの Unity イベントが送信されたときに、ボタンが押されたとき、または解放されたときに、状態に履歴情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="feb58-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="feb58-170">スロー中に正確なコントローラーレンダリングとコントローラーターゲットを取得するには、必要に応じて、ポーリングとイベントを正しく使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="feb58-171">コントローラーが各フレームを **レンダリング** する場合、アプリは、現在のフレームの photon 時間に合わせて、コントローラーの *オブジェクト* を前方予測コントローラーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="feb58-172">このデータは、XR のような Unity ポーリング Api から取得し *[ます。InputTracking。 GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* または *[XR。付い.GetCurrentReading を入力し](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* ます。</span><span class="sxs-lookup"><span data-stu-id="feb58-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="feb58-173">プレスまたはリリースを対象とする **コントローラー** の場合、アプリは、そのプレスまたはリリースイベントのコントローラーの履歴に基づいて、軌道を raycast して計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="feb58-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="feb58-174">このデータは、Interactionmanager と同様に Unity イベント Api から取得し *[ます。 Interactionsource押さ](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* れています。</span><span class="sxs-lookup"><span data-stu-id="feb58-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="feb58-175">**グリップを使用** します。</span><span class="sxs-lookup"><span data-stu-id="feb58-175">**Use the grip pose**.</span></span> <span data-ttu-id="feb58-176">角速度とベロシティは、ポインターではなく、グリップによって報告されます。</span><span class="sxs-lookup"><span data-stu-id="feb58-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="feb58-177">今後の Windows 更新プログラムでは、のスローが引き続き改善され、詳細についてはここで確認できます。</span><span class="sxs-lookup"><span data-stu-id="feb58-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="feb58-178">MRTK v2 のジェスチャとモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="feb58-178">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="feb58-179">入力マネージャーからジェスチャとモーションコントローラーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="feb58-179">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="feb58-180">MRTK v2 でのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="feb58-180">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="feb58-181">MRTK v2 のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="feb58-181">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="feb58-182">チュートリアルに従う</span><span class="sxs-lookup"><span data-stu-id="feb58-182">Follow along with tutorials</span></span>

<span data-ttu-id="feb58-183">詳細なカスタマイズ例が記載されたステップバイステップのチュートリアルは、Mixed Reality Academy でご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="feb58-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="feb58-184">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="feb58-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="feb58-185">MR 入力 213:モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="feb58-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="feb58-186">[![MR 入力 213-モーションコントローラー](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="feb58-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="feb58-187">*MR 入力 213-モーションコントローラー*</span><span class="sxs-lookup"><span data-stu-id="feb58-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="feb58-188">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="feb58-188">Next Development Checkpoint</span></span>

<span data-ttu-id="feb58-189">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="feb58-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="feb58-190">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="feb58-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="feb58-191">手と視線の追跡</span><span class="sxs-lookup"><span data-stu-id="feb58-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="feb58-192">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="feb58-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="feb58-193">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="feb58-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="feb58-194">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="feb58-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="feb58-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="feb58-195">See also</span></span>

* [<span data-ttu-id="feb58-196">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="feb58-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="feb58-197">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="feb58-197">Motion controllers</span></span>](../../design/motion-controllers.md)