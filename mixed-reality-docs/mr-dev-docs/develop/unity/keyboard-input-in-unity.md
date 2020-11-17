---
title: Unity でのキーボード入力
description: Unity には、使用可能な物理キーボードがない場合にキーボード入力を受け入れるための TouchScreenKeyboard クラスが用意されています。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: キーボード、入力、unity、touchscreenkeyboard、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: aa9bb3059a8d0cc5b829bf14d92928511259b7f9
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677421"
---
# <a name="keyboard-input-in-unity"></a>Unity でのキーボード入力

**名前空間:** *unityengine*<br>
 **型**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens では、Bluetooth キーボードを含む多くの形式の入力がサポートされますが、ほとんどのアプリケーションでは、すべてのユーザーが物理キーボードを使用できると想定することはできません。 アプリケーションでテキスト入力が必要な場合は、スクリーンキーボードの何らかの形式を指定する必要があります。

Unity には、使用可能な物理キーボードがない場合にキーボード入力を受け入れるための *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* クラスが用意されています。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity での HoloLens システムキーボード動作

HoloLens では、 *TouchScreenKeyboard* はシステムのスクリーンキーボードを活用します。 システムのスクリーンキーボードを容量ビューの上に重ねて表示することはできません。そのため、Unity では、入力が送信された後にキーボードを表示するセカンダリ 2D XAML ビューを作成してから容量ビューに戻る必要があります。 ユーザーフローは次のようになります。
1. ユーザーがアクションを実行して、アプリコードが *TouchScreenKeyboard* を呼び出すようにします。
    * アプリは、 *TouchScreenKeyboard* を呼び出す前にアプリの状態を一時停止します。
    * 容量ビューに切り替える前に、アプリを終了することがあります
2. Unity は、世界中に自動的に配置される 2D XAML ビューに切り替えます。
3. ユーザーはシステムキーボードを使用してテキストを入力し、送信またはキャンセルします。
4. Unity は容量ビューに戻ります。
    * *TouchScreenKeyboard* が完了すると、アプリはアプリの状態を再開する役割を担います。
5. 送信されたテキストは、 *TouchScreenKeyboard* で入手できます。

### <a name="available-keyboard-views"></a>使用可能なキーボードビュー

次の6つの異なるキーボードビューを使用できます。
* 単一行のテキストボックス
* タイトル付きの単一行テキストボックス
* 複数行のテキストボックス
* タイトルを含む複数行のテキストボックス
* 単一行パスワードボックス
* タイトル付きの単一行パスワードボックス

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Unity でシステムキーボードを有効にする方法

HoloLens システムキーボードは、"UWP ビルドの種類" を "XAML" に設定してエクスポートされた Unity アプリケーションに対してのみ使用できます。 "D3D" で "UWP ビルドの種類" として "XAML" を選択すると、トレードオフが発生します。 これらのトレードオフに慣れていない場合は、システムキーボードの [代替入力ソリューション](#alternative-keyboard-options) を調べることをお勧めします。
1. [**ファイル**] メニューを開き、[**ビルドの設定**] を選択します。
2. **プラットフォーム** が **Windows ストア** に設定されていること、 **SDK** が **Universal 10** に設定されていること、 **UWP ビルドの種類** を **XAML** に設定していることを確認します。
3. [ **ビルドの設定** ] ダイアログボックスで、[ **プレーヤーの設定...** ] ボタンをクリックします。
4. [ **Windows ストアの設定** ] タブを選択します。
5. [ **その他の設定** ] グループを展開します。
6. [ **表示** ] セクションで、[ **サポートされている仮想現実** ] チェックボックスをオンにして、新しい **仮想現実デバイス** の一覧を追加します。
7. Virtual Reality Sdk の一覧に [ **Windows Holographic** ] が表示されていることを確認します。

>[!NOTE]
>HoloLens デバイスでサポートされている仮想現実としてビルドをマークしない場合、プロジェクトは 2D XAML アプリとしてエクスポートされます。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity アプリでのシステムキーボードの使用

### <a name="declare-the-keyboard"></a>キーボードを宣言する

クラスで、 *TouchScreenKeyboard* と、キーボードが返す文字列を保持する変数を格納する変数を宣言します。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>キーボードを呼び出す

キーボード入力を要求するイベントが発生したときに、必要な入力の種類に応じて、これらの関数のいずれかを呼び出します。 タイトルは textPlaceholder パラメーターで指定されていることに注意してください。

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>型指定されたコンテンツの取得

Update ループで、キーボードが新しい入力を受け取ったかどうかを確認し、別の場所で使用するために保存します。

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.status == TouchScreenKeyboard.Status.Done)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>代替キーボードオプション

容量ビューから2D ビューへの切り替えは、ユーザーからのテキスト入力を取得するのに最適な方法ではないことを理解しています。

Unity を通じてシステムキーボードを利用するための現在の代替手段は次のとおりです。
* 入力に音声ディクテーションを使用する (<b>注:</b> 辞書に見つからず、パスワード入力に適していない単語に対してはエラーが発生する可能性があります)
* アプリケーションの排他ビューで動作するキーボードを作成する

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality プラットフォームの機能と Api の調査が途中で終了しています。 ここから、任意の [トピック](unity-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接進むことができます。

> [!div class="nextstepaction"]
> [HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ](../platform-capabilities-and-apis/using-visual-studio.md)
