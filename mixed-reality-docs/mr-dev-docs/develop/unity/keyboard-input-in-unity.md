---
title: Unity でのキーボード入力
description: Unity には、使用可能な物理キーボードがないときにキーボード入力を受け入れるための TouchScreenKeyboard クラスが用意されています。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: キーボード、入力、unity、touchscreenkeyboard、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 613c9327b517205c340555b6423a3809906f9b9f
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010513"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="96186-104">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="96186-104">Keyboard input in Unity</span></span>

<span data-ttu-id="96186-105">**名前空間:** *unityengine*</span><span class="sxs-lookup"><span data-stu-id="96186-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="96186-106">**型**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="96186-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="96186-107">HoloLens では、Bluetooth キーボードを含む多くの形式の入力がサポートされますが、ほとんどのアプリケーションでは、すべてのユーザーが物理キーボードを使用できると想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="96186-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="96186-108">アプリケーションでテキスト入力が必要な場合は、スクリーンキーボードの何らかの形式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96186-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="96186-109">Unity には、使用可能な物理キーボードがないときにキーボード入力を受け入れるための *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="96186-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="96186-110">Unity での HoloLens システムキーボード動作</span><span class="sxs-lookup"><span data-stu-id="96186-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="96186-111">HoloLens では、 *TouchScreenKeyboard* はシステムのスクリーンキーボードを活用します。</span><span class="sxs-lookup"><span data-stu-id="96186-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard.</span></span> <span data-ttu-id="96186-112">システムのスクリーンキーボードを容量ビューの上に重ねて表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="96186-112">The system's on-screen keyboard can't overlay on top of a volumetric view.</span></span> <span data-ttu-id="96186-113">Unity では、入力が送信されたら、キーボードを表示して容量ビューに戻るために、セカンダリ 2D XAML ビューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96186-113">Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="96186-114">ユーザーフローは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="96186-114">The user flow goes like this:</span></span>
1. <span data-ttu-id="96186-115">ユーザーがアクションを実行して、アプリコードが *TouchScreenKeyboard* を呼び出すようにします。</span><span class="sxs-lookup"><span data-stu-id="96186-115">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="96186-116">アプリは、 *TouchScreenKeyboard* を呼び出す前にアプリの状態を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="96186-116">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="96186-117">容量ビューに切り替える前に、アプリを終了することがあります</span><span class="sxs-lookup"><span data-stu-id="96186-117">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="96186-118">Unity は、世界中に自動配置される 2D XAML ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="96186-118">Unity switches to a 2D XAML view, which is autoplaced in the world</span></span>
3. <span data-ttu-id="96186-119">ユーザーはシステムキーボードを使用してテキストを入力し、送信またはキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="96186-119">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="96186-120">Unity は容量ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="96186-120">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="96186-121">*TouchScreenKeyboard* が完了すると、アプリはアプリの状態を再開する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="96186-121">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="96186-122">送信されたテキストは、 *TouchScreenKeyboard* で入手できます。</span><span class="sxs-lookup"><span data-stu-id="96186-122">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="96186-123">使用可能なキーボードビュー</span><span class="sxs-lookup"><span data-stu-id="96186-123">Available keyboard views</span></span>

<span data-ttu-id="96186-124">次の6つの異なるキーボードビューを使用できます。</span><span class="sxs-lookup"><span data-stu-id="96186-124">There are six different keyboard views available:</span></span>
* <span data-ttu-id="96186-125">単一行のテキストボックス</span><span class="sxs-lookup"><span data-stu-id="96186-125">Single-line textbox</span></span>
* <span data-ttu-id="96186-126">タイトル付きの単一行テキストボックス</span><span class="sxs-lookup"><span data-stu-id="96186-126">Single-line textbox with title</span></span>
* <span data-ttu-id="96186-127">複数行のテキストボックス</span><span class="sxs-lookup"><span data-stu-id="96186-127">Multi-line textbox</span></span>
* <span data-ttu-id="96186-128">タイトルを含む複数行のテキストボックス</span><span class="sxs-lookup"><span data-stu-id="96186-128">Multi-line textbox with title</span></span>
* <span data-ttu-id="96186-129">単一行パスワードボックス</span><span class="sxs-lookup"><span data-stu-id="96186-129">Single-line password box</span></span>
* <span data-ttu-id="96186-130">タイトル付きの単一行パスワードボックス</span><span class="sxs-lookup"><span data-stu-id="96186-130">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="96186-131">Unity でシステムキーボードを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="96186-131">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="96186-132">HoloLens システムキーボードは、"UWP ビルドの種類" を "XAML" に設定してエクスポートされた Unity アプリケーションに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="96186-132">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="96186-133">"D3D" で "UWP ビルドの種類" として "XAML" を選択すると、トレードオフが発生します。</span><span class="sxs-lookup"><span data-stu-id="96186-133">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="96186-134">これらのトレードオフに慣れていない場合は、システムキーボードの [代替入力ソリューション](#alternative-keyboard-options) を調べることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="96186-134">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="96186-135">[**ファイル**] メニューを開き、[**ビルドの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="96186-135">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="96186-136">**プラットフォーム** が **Windows ストア** に設定されていること、 **SDK** が **Universal 10** に設定されていること、 **UWP ビルドの種類** を **XAML** に設定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96186-136">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="96186-137">[ **ビルドの設定** ] ダイアログボックスで、[ **プレーヤーの設定...** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="96186-137">In the **Build Settings** dialog, select the **Player Settings...** button</span></span>
4. <span data-ttu-id="96186-138">[ **Windows ストアの設定** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="96186-138">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="96186-139">[ **その他の設定** ] グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="96186-139">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="96186-140">[ **表示** ] セクションで、[ **サポートされている仮想現実** ] チェックボックスをオンにして、新しい **仮想現実デバイス** の一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="96186-140">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="96186-141">Virtual Reality Sdk の一覧に [ **Windows Holographic** ] が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96186-141">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="96186-142">HoloLens デバイスでサポートされている仮想現実としてビルドをマークしない場合、プロジェクトは 2D XAML アプリとしてエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="96186-142">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="96186-143">Unity アプリでのシステムキーボードの使用</span><span class="sxs-lookup"><span data-stu-id="96186-143">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="96186-144">キーボードを宣言する</span><span class="sxs-lookup"><span data-stu-id="96186-144">Declare the keyboard</span></span>

<span data-ttu-id="96186-145">クラスで、 *TouchScreenKeyboard* と、キーボードが返す文字列を保持する変数を格納する変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="96186-145">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="96186-146">キーボードを呼び出す</span><span class="sxs-lookup"><span data-stu-id="96186-146">Invoke the keyboard</span></span>

<span data-ttu-id="96186-147">キーボード入力を要求するイベントが発生したときに、textPlaceholder パラメーターのタイトルを使用して、必要な入力の種類に応じて、これらの関数のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="96186-147">When an event occurs requesting keyboard input, call one of these functions depending on the type of input you want using the title in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="96186-148">型指定されたコンテンツの取得</span><span class="sxs-lookup"><span data-stu-id="96186-148">Retrieve typed contents</span></span>

<span data-ttu-id="96186-149">Update ループで、キーボードが新しい入力を受け取ったかどうかを確認し、別の場所で使用するために保存します。</span><span class="sxs-lookup"><span data-stu-id="96186-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="96186-150">代替キーボードオプション</span><span class="sxs-lookup"><span data-stu-id="96186-150">Alternative keyboard options</span></span>

<span data-ttu-id="96186-151">容量ビューから2D ビューへの切り替えは、ユーザーからのテキスト入力を取得するのに最適な方法ではないことを理解しています。</span><span class="sxs-lookup"><span data-stu-id="96186-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="96186-152">Unity を通じてシステムキーボードを利用するための現在の代替手段は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="96186-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="96186-153">入力に音声ディクテーションを使用する (<b>注:</b> 辞書に見つからず、パスワード入力に適さない単語には間違いが発生する可能性があります)</span><span class="sxs-lookup"><span data-stu-id="96186-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and isn't suitable for password entry)</span></span>
* <span data-ttu-id="96186-154">アプリケーションの排他ビューで動作するキーボードを作成する</span><span class="sxs-lookup"><span data-stu-id="96186-154">Create a keyboard that works in your applications exclusive view</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="96186-155">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="96186-155">Next Development Checkpoint</span></span>

<span data-ttu-id="96186-156">これまでに説明した Unity 開発の取り組みに従っている場合は、Mixed Reality プラットフォームの機能と Api を試してみることになります。</span><span class="sxs-lookup"><span data-stu-id="96186-156">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="96186-157">ここからは、任意の [トピック](unity-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接ジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="96186-157">From here, you can continue to any [topic](unity-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="96186-158">HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="96186-158">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
