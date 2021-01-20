---
title: DirectX でのキーボード、マウス、およびコントローラー入力
description: キーボード、マウス、およびゲームコントローラーを使用する Windows Mixed Reality 用のアプリを作成する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, キーボード, マウス, ゲームコントローラー, xbox コントローラー, HoloLens, デスクトップ, チュートリアル, サンプルコード
ms.openlocfilehash: 3cf35ba195e839332cbedb8b2c3945334a158cbc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583635"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="94e53-104">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="94e53-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="94e53-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="94e53-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="94e53-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94e53-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="94e53-107">Windows Mixed Reality デバイスでは、キーボード、マウス、およびゲームコントローラーはすべて、便利な入力形式です。</span><span class="sxs-lookup"><span data-stu-id="94e53-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="94e53-108">Bluetooth キーボードとマウスは両方とも HoloLens でサポートされており、アプリのデバッグや別の入力形式として使用できます。</span><span class="sxs-lookup"><span data-stu-id="94e53-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="94e53-109">Windows Mixed Reality では、Pc に接続されているイマーシブヘッドセットもサポートされています。マウス、キーボード、およびゲームコントローラーは、従来は標準でした。</span><span class="sxs-lookup"><span data-stu-id="94e53-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="94e53-110">HoloLens でキーボード入力を使用するには、Bluetooth キーボードをデバイスにペアリングするか、Windows デバイスポータルを使用して仮想入力を使用します。</span><span class="sxs-lookup"><span data-stu-id="94e53-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="94e53-111">Windows Mixed Reality のイマーシブヘッドセットを装着しているときにキーボード入力を使用するには、をデバイスに配置するか、Windows キーと Y キーの組み合わせを使用して、混合現実に入力フォーカスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="94e53-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="94e53-112">HoloLens 用のアプリは、これらのデバイスが接続されていない機能を提供する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="94e53-113">この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。</span><span class="sxs-lookup"><span data-stu-id="94e53-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="94e53-114">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94e53-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="94e53-115">CoreWindow 入力イベントをサブスクライブします</span><span class="sxs-lookup"><span data-stu-id="94e53-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="94e53-116">キーボード入力</span><span class="sxs-lookup"><span data-stu-id="94e53-116">Keyboard input</span></span>

<span data-ttu-id="94e53-117">Windows Holographic アプリテンプレートでは、他の UWP アプリと同じように、キーボード入力用のイベントハンドラーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="94e53-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="94e53-118">アプリでは、Windows Mixed Reality と同じ方法でキーボード入力データを使用します。</span><span class="sxs-lookup"><span data-stu-id="94e53-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="94e53-119">AppView .cpp から:</span><span class="sxs-lookup"><span data-stu-id="94e53-119">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="94e53-120">仮想キーボード入力</span><span class="sxs-lookup"><span data-stu-id="94e53-120">Virtual keyboard input</span></span>
<span data-ttu-id="94e53-121">イマーシブデスクトップヘッドセットの場合は、 **CoreTextEditContext** を実装することにより、イマーシブビューで Windows によってレンダリングされる仮想キーボードをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="94e53-121">For immersive desktop headsets, you can support virtual keyboards rendered by Windows over your immersive view by implementing **CoreTextEditContext**.</span></span> <span data-ttu-id="94e53-122">これにより、Windows はアプリでレンダリングされたテキストボックスの状態を把握できるようになり、仮想キーボードがそこにあるテキストに正しく参加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="94e53-122">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="94e53-123">CoreTextEditContext サポートの実装の詳細については、 [CoreTextEditContext サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-123">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="94e53-124">マウス入力</span><span class="sxs-lookup"><span data-stu-id="94e53-124">Mouse Input</span></span>

<span data-ttu-id="94e53-125">また、UWP CoreWindow 入力イベントハンドラーを使用して、マウス入力を再度使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="94e53-125">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="94e53-126">ここでは、Windows Holographic アプリケーションテンプレートを変更して、マウスのクリック操作を、押したジェスチャと同じようにサポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94e53-126">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="94e53-127">この変更を行った後、イマーシブヘッドセットデバイスの装着中にマウスをクリックすると、キューブが再配置されます。</span><span class="sxs-lookup"><span data-stu-id="94e53-127">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

> [!NOTE]
> <span data-ttu-id="94e53-128">UWP アプリでは、 [Mousedevice](/uwp/api/Windows.Devices.Input.MouseDevice) API を使用して、マウスの生の XY データを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="94e53-128">UWP apps can also get raw XY data for the mouse by using the [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="94e53-129">まず、AppView. h で新しい Onポインタ押されたハンドラーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="94e53-129">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="94e53-130">AppView .cpp で、次のコードを SetWindow に追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-130">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="94e53-131">次に、この定義を、ファイルの末尾で押された Onポインタに配置します。</span><span class="sxs-lookup"><span data-stu-id="94e53-131">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="94e53-132">追加したイベントハンドラーは、テンプレートのメインクラスへのパススルーです。</span><span class="sxs-lookup"><span data-stu-id="94e53-132">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="94e53-133">このパススルーをサポートするようにメインクラスを変更してみましょう。</span><span class="sxs-lookup"><span data-stu-id="94e53-133">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="94e53-134">次のパブリックメソッド宣言をヘッダーファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-134">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="94e53-135">このプライベートメンバー変数も必要になります。</span><span class="sxs-lookup"><span data-stu-id="94e53-135">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="94e53-136">最後に、メインクラスを新しいロジックで更新して、マウスのクリックをサポートします。</span><span class="sxs-lookup"><span data-stu-id="94e53-136">Finally, we'll update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="94e53-137">まず、このイベントハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-137">Start by adding this event handler.</span></span> <span data-ttu-id="94e53-138">クラス名を必ず更新してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-138">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="94e53-139">次に、Update メソッドで、ポインターを取得するための既存のロジックを次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="94e53-139">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="94e53-140">再コンパイルして再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="94e53-140">Recompile and redeploy.</span></span> <span data-ttu-id="94e53-141">マウスをクリックすると、bluetooth マウスが接続されているイマーシブヘッドセットまたは HoloLens のキューブが再配置されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-141">Notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="94e53-142">ゲームコントローラーのサポート</span><span class="sxs-lookup"><span data-stu-id="94e53-142">Game controller support</span></span>

<span data-ttu-id="94e53-143">ゲームコントローラーは、ユーザーがイマーシブ Windows Mixed Reality エクスペリエンスを制御できる楽しい便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="94e53-143">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

 <span data-ttu-id="94e53-144">メインファイルの header クラスに次のプライベートメンバー宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-144">add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="94e53-145">メインクラスのコンストラクターで、ゲームパッドイベントと、現在アタッチされているすべてのゲームパッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="94e53-145">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="94e53-146">これらのイベントハンドラーを main クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-146">Add these event handlers to your main class.</span></span> <span data-ttu-id="94e53-147">クラス名を必ず更新してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-147">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="94e53-148">最後に、コントローラーの状態の変更を認識するように入力ロジックを更新します。</span><span class="sxs-lookup"><span data-stu-id="94e53-148">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="94e53-149">ここでは、前のセクションで説明したのと同じ m_pointerPressed 変数を使用して、マウスイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-149">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="94e53-150">SpatialPointerPose をチェックする直前に、Update メソッドに次を追加します。</span><span class="sxs-lookup"><span data-stu-id="94e53-150">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="94e53-151">メインクラスをクリーンアップするときは、必ずイベントの登録を解除してください。</span><span class="sxs-lookup"><span data-stu-id="94e53-151">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="94e53-152">再コンパイルし、再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="94e53-152">Recompile, and redeploy.</span></span> <span data-ttu-id="94e53-153">これで、ゲームコントローラーをアタッチまたはペアリングし、回転するキューブの位置を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="94e53-153">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="94e53-154">キーボードとマウスの入力に関する重要なガイドライン</span><span class="sxs-lookup"><span data-stu-id="94e53-154">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="94e53-155">Microsoft HoloLens でこのコードを使用する方法には、主な違いがいくつかあります。これは、主に自然なユーザー入力に依存するデバイスであり、Windows Mixed Reality 対応 PC で使用できるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="94e53-155">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="94e53-156">キーボードやマウスの入力に依存することはできません。</span><span class="sxs-lookup"><span data-stu-id="94e53-156">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="94e53-157">アプリのすべての機能は、宝石、ジェスチャ、音声入力で動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94e53-157">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="94e53-158">Bluetooth キーボードが接続されている場合は、アプリが要求するテキストに対してキーボード入力を有効にすると便利です。</span><span class="sxs-lookup"><span data-stu-id="94e53-158">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="94e53-159">これは、たとえば、ディクテーションの優れた補完です。</span><span class="sxs-lookup"><span data-stu-id="94e53-159">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="94e53-160">アプリを設計する際には、ゲームのために (たとえば) WASD やマウスのコントロールを使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="94e53-160">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="94e53-161">HoloLens は、ユーザーが部屋を移動するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="94e53-161">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="94e53-162">この場合、ユーザーはカメラを直接制御します。</span><span class="sxs-lookup"><span data-stu-id="94e53-162">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="94e53-163">移動/表示コントロールを使用して、部屋の周りにカメラを運転するためのインターフェイスは、同じエクスペリエンスを提供しません。</span><span class="sxs-lookup"><span data-stu-id="94e53-163">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="94e53-164">キーボード入力は、特にユーザーがキーボードを使用する必要がないため、アプリまたはゲームエンジンのデバッグを制御する優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="94e53-164">Keyboard input is an excellent way to control your app or game engine debugging, especially since the user won't be required to use the keyboard.</span></span> <span data-ttu-id="94e53-165">この配線は、CoreWindow イベント Api を使用した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="94e53-165">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="94e53-166">このシナリオでは、デバッグセッション中にキーボードイベントを "デバッグ入力のみ" モードにルーティングするようにアプリを構成する方法を実装することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="94e53-166">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="94e53-167">Bluetooth コントローラーも同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="94e53-167">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="94e53-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="94e53-168">See also</span></span>
* [<span data-ttu-id="94e53-169">ハードウェア アクセサリ</span><span class="sxs-lookup"><span data-stu-id="94e53-169">Hardware accessories</span></span>](../../discover/hardware-accessories.md)