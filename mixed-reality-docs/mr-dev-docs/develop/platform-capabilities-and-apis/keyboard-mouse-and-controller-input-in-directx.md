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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX でのキーボード、マウス、およびコントローラー入力

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。

Windows Mixed Reality デバイスでは、キーボード、マウス、およびゲームコントローラーはすべて、便利な入力形式です。 Bluetooth キーボードとマウスは両方とも HoloLens でサポートされており、アプリのデバッグや別の入力形式として使用できます。 Windows Mixed Reality では、Pc に接続されているイマーシブヘッドセットもサポートされています。マウス、キーボード、およびゲームコントローラーは、従来は標準でした。

HoloLens でキーボード入力を使用するには、Bluetooth キーボードをデバイスにペアリングするか、Windows デバイスポータルを使用して仮想入力を使用します。 Windows Mixed Reality のイマーシブヘッドセットを装着しているときにキーボード入力を使用するには、をデバイスに配置するか、Windows キーと Y キーの組み合わせを使用して、混合現実に入力フォーカスを割り当てます。 HoloLens 用のアプリは、これらのデバイスが接続されていない機能を提供する必要があることに注意してください。

>[!NOTE]
>この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

## <a name="subscribe-for-corewindow-input-events"></a>CoreWindow 入力イベントをサブスクライブします

### <a name="keyboard-input"></a>キーボード入力

Windows Holographic アプリテンプレートでは、他の UWP アプリと同じように、キーボード入力用のイベントハンドラーが追加されています。 アプリでは、Windows Mixed Reality と同じ方法でキーボード入力データを使用します。

AppView .cpp から:

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

### <a name="virtual-keyboard-input"></a>仮想キーボード入力
イマーシブデスクトップヘッドセットの場合は、 **CoreTextEditContext** を実装することにより、イマーシブビューで Windows によってレンダリングされる仮想キーボードをサポートできます。 これにより、Windows はアプリでレンダリングされたテキストボックスの状態を把握できるようになり、仮想キーボードがそこにあるテキストに正しく参加できるようになります。

CoreTextEditContext サポートの実装の詳細については、 [CoreTextEditContext サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)を参照してください。

### <a name="mouse-input"></a>マウス入力

また、UWP CoreWindow 入力イベントハンドラーを使用して、マウス入力を再度使用することもできます。 ここでは、Windows Holographic アプリケーションテンプレートを変更して、マウスのクリック操作を、押したジェスチャと同じようにサポートする方法について説明します。 この変更を行った後、イマーシブヘッドセットデバイスの装着中にマウスをクリックすると、キューブが再配置されます。

> [!NOTE]
> UWP アプリでは、 [Mousedevice](/uwp/api/Windows.Devices.Input.MouseDevice) API を使用して、マウスの生の XY データを取得することもできます。

まず、AppView. h で新しい Onポインタ押されたハンドラーを宣言します。

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

AppView .cpp で、次のコードを SetWindow に追加します。

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

次に、この定義を、ファイルの末尾で押された Onポインタに配置します。

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

追加したイベントハンドラーは、テンプレートのメインクラスへのパススルーです。 このパススルーをサポートするようにメインクラスを変更してみましょう。 次のパブリックメソッド宣言をヘッダーファイルに追加します。

```
// Handle mouse input.
       void OnPointerPressed();
```

このプライベートメンバー変数も必要になります。

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最後に、メインクラスを新しいロジックで更新して、マウスのクリックをサポートします。 まず、このイベントハンドラーを追加します。 クラス名を必ず更新してください。

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

次に、Update メソッドで、ポインターを取得するための既存のロジックを次のように置き換えます。

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

再コンパイルして再デプロイします。 マウスをクリックすると、bluetooth マウスが接続されているイマーシブヘッドセットまたは HoloLens のキューブが再配置されることに注意してください。

### <a name="game-controller-support"></a>ゲームコントローラーのサポート

ゲームコントローラーは、ユーザーがイマーシブ Windows Mixed Reality エクスペリエンスを制御できる楽しい便利な方法です。

 メインファイルの header クラスに次のプライベートメンバー宣言を追加します。

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

メインクラスのコンストラクターで、ゲームパッドイベントと、現在アタッチされているすべてのゲームパッドを初期化します。

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

これらのイベントハンドラーを main クラスに追加します。 クラス名を必ず更新してください。

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

最後に、コントローラーの状態の変更を認識するように入力ロジックを更新します。 ここでは、前のセクションで説明したのと同じ m_pointerPressed 変数を使用して、マウスイベントを追加します。 SpatialPointerPose をチェックする直前に、Update メソッドに次を追加します。

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

メインクラスをクリーンアップするときは、必ずイベントの登録を解除してください。

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

再コンパイルし、再デプロイします。 これで、ゲームコントローラーをアタッチまたはペアリングし、回転するキューブの位置を変更することができます。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>キーボードとマウスの入力に関する重要なガイドライン

Microsoft HoloLens でこのコードを使用する方法には、主な違いがいくつかあります。これは、主に自然なユーザー入力に依存するデバイスであり、Windows Mixed Reality 対応 PC で使用できるものと同じです。
* キーボードやマウスの入力に依存することはできません。 アプリのすべての機能は、宝石、ジェスチャ、音声入力で動作する必要があります。
* Bluetooth キーボードが接続されている場合は、アプリが要求するテキストに対してキーボード入力を有効にすると便利です。 これは、たとえば、ディクテーションの優れた補完です。
* アプリを設計する際には、ゲームのために (たとえば) WASD やマウスのコントロールを使用しないようにしてください。 HoloLens は、ユーザーが部屋を移動するように設計されています。 この場合、ユーザーはカメラを直接制御します。 移動/表示コントロールを使用して、部屋の周りにカメラを運転するためのインターフェイスは、同じエクスペリエンスを提供しません。
* キーボード入力は、特にユーザーがキーボードを使用する必要がないため、アプリまたはゲームエンジンのデバッグを制御する優れた方法です。 この配線は、CoreWindow イベント Api を使用した場合と同じです。 このシナリオでは、デバッグセッション中にキーボードイベントを "デバッグ入力のみ" モードにルーティングするようにアプリを構成する方法を実装することを選択できます。
* Bluetooth コントローラーも同様に機能します。

## <a name="see-also"></a>関連項目
* [ハードウェア アクセサリ](../../discover/hardware-accessories.md)