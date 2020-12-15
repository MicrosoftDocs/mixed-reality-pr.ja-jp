---
title: Windows Mixed Reality シミュレーターを使用する
description: Windows Mixed Reality シミュレーターを使用すると、Windows Mixed Reality のイマーシブヘッドセットを使用せずに、お使いの PC で mixed reality アプリをテストすることができます。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality、シミュレーター、テスト
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530294"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="0d22c-104">Windows Mixed Reality シミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="0d22c-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="0d22c-105">Windows Mixed Reality シミュレーターを使用すると、Windows Mixed Reality のイマーシブヘッドセットを使用せずに、お使いの PC で mixed reality アプリをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="0d22c-106">シミュレーターは、Windows 10 の作成者の更新プログラムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-106">The simulator is available with the Windows 10 Creators Update.</span></span> <span data-ttu-id="0d22c-107">シミュレーターは [HoloLens エミュレーター](using-the-hololens-emulator.md)に似ていますが、シミュレーターでは仮想マシンが使用されません。</span><span class="sxs-lookup"><span data-stu-id="0d22c-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator doesn't use a virtual machine.</span></span> <span data-ttu-id="0d22c-108">シミュレートされたアプリは、イマーシブヘッドセットを使用している場合と同じように、Windows 10 デスクトップのユーザーセッションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-108">Simulated apps run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="0d22c-109">イマーシブヘッドセットのセンサーによって読み取られた人間と環境の入力は、キーボード、マウス、または Xbox コントローラーを使用してシミュレートされます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-109">The human and environmental inputs read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="0d22c-110">アプリは、シミュレーターで実行するための変更を必要とせず、イマーシブヘッドセットで実行されていないことを認識していません。</span><span class="sxs-lookup"><span data-stu-id="0d22c-110">Apps don't need any modification to run in the simulator, and don't know they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="0d22c-111">Windows Mixed Reality シミュレーターの有効化</span><span class="sxs-lookup"><span data-stu-id="0d22c-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="0d22c-112">開発者向けの設定から **開発者モードを有効にする**-> の更新プログラムとセキュリティ-></span><span class="sxs-lookup"><span data-stu-id="0d22c-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="0d22c-113">デスクトップから **Mixed Reality ポータル** を起動する</span><span class="sxs-lookup"><span data-stu-id="0d22c-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="0d22c-114">ポータルを初めて起動する場合は、セットアップエクスペリエンスを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d22c-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="0d22c-115">[**作業の開始**] を選択する</span><span class="sxs-lookup"><span data-stu-id="0d22c-115">Select **Get started**</span></span>
   2. <span data-ttu-id="0d22c-116">[ **契約に同意する] を** 選択します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-116">Select **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="0d22c-117">物理デバイスを使用せずにセットアップを続行するには、[ **シミュレーション用に設定 (開発者向け)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-117">Select **Set up for simulation (for developers)** to continue through setup without a physical device</span></span>
   4. <span data-ttu-id="0d22c-118">選択内容を確認するには、 **[セットアップ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-118">Select **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="0d22c-119">Mixed Reality ポータルの左側にある [ **開発者向け** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-119">Select the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="0d22c-120">シミュレーション切り替え **スイッチをオンにする**</span><span class="sxs-lookup"><span data-stu-id="0d22c-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="0d22c-121">シミュレーションを有効にすると、既定では、シミュレートされた6つの自由可能なコントローラーの左側が有効になります。</span><span class="sxs-lookup"><span data-stu-id="0d22c-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="0d22c-122">Windows 10 が2019に更新される前に、シミュレートされた6自由コントローラーをインストールするには、管理者のアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="0d22c-122">Before the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="0d22c-123">[ユーザーアカウント制御] ダイアログボックスが表示されたら、そのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-123">Accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="0d22c-124">これでシミュレーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-124">You should now be running with simulation!</span></span>

<span data-ttu-id="0d22c-125">[設定] で開発者モードを無効にする場合は、まず、Mixed Reality ポータルの [**開発者向け**] セクションで、シミュレーション切り替えスイッチを [**オフ**] に切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d22c-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="0d22c-126">混合の現実シミュレーターへのアプリの配置</span><span class="sxs-lookup"><span data-stu-id="0d22c-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="0d22c-127">シミュレーターは仮想マシンを使用せずにローカル PC で実行されるため、デバッグ時にユニバーサル Windows アプリを **ローカルコンピューター** に配置できます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-127">Since the simulator runs on your local PC without a Virtual Machine, you can deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="0d22c-128">基本的なシミュレーター入力</span><span class="sxs-lookup"><span data-stu-id="0d22c-128">Basic simulator input</span></span>

<span data-ttu-id="0d22c-129">シミュレーターの制御は、多くの一般的な3D ビデオゲームと [HoloLens エミュレーター](using-the-hololens-emulator.md)に似ています。</span><span class="sxs-lookup"><span data-stu-id="0d22c-129">Controlling the simulator is similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="0d22c-130">入力オプションは、キーボード、マウス、または Xbox コントローラーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="0d22c-131">シミュレートされたユーザーがイマーシブヘッドセットを装着したときのアクションを指示することによって、シミュレーターを制御します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="0d22c-132">操作を実行すると、シミュレートされたユーザーが移動され、イマーシブヘッドセットの場合と同じように応答するアプリとの対話が行われます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="0d22c-133">**前後左右に歩く** - キーボードの W、A、S、D キーまたは Xbox コントローラーの左スティックを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="0d22c-134">[**検索]、[下]、[左]、[右**] の順に選択してドラッグし、キーボードの方向キーを押すか、Xbox コントローラーの右スティックを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-134">**Look up, down, left, and right** - Select and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="0d22c-135">**コントローラーでのアクションボタンの押下** -マウスを右クリックするか、キーボードの enter キーを押すか、または Xbox コントローラーの A ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="0d22c-136">**[ホーム] ボタン** をクリックしてコントローラーを押す-キーボードの Windows キーまたは F2 キーを押すか、Xbox コントローラーの B ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="0d22c-137">**スクロール用のコントローラーの移動** -Alt キーとマウスの右ボタンを押したまま、マウスを上下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0d22c-137">**Controller movement for scrolling** - Hold the Alt key and the right mouse button, then drag the mouse up / down.</span></span> <span data-ttu-id="0d22c-138">Xbox コントローラーで、右のトリガーとボタンを押したまま、右スティックを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="0d22c-138">In an Xbox controller, hold down the right trigger and A button and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="0d22c-139">追跡対象のコントローラー</span><span class="sxs-lookup"><span data-stu-id="0d22c-139">Tracked controllers</span></span>

<span data-ttu-id="0d22c-140">Mixed Reality シミュレーターでは、最大2つのハンド保持された追跡対象モーションコントローラーをシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-140">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="0d22c-141">混合 Reality ポータルで切り替えスイッチを使用して有効にします。</span><span class="sxs-lookup"><span data-stu-id="0d22c-141">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="0d22c-142">各シミュレートされたコントローラーには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="0d22c-142">Each simulated controller has:</span></span>
* <span data-ttu-id="0d22c-143">空間内の位置と向き</span><span class="sxs-lookup"><span data-stu-id="0d22c-143">Position and orientation in space</span></span>
* <span data-ttu-id="0d22c-144">ホーム ボタン</span><span class="sxs-lookup"><span data-stu-id="0d22c-144">Home button</span></span>
* <span data-ttu-id="0d22c-145">メニュー ボタン</span><span class="sxs-lookup"><span data-stu-id="0d22c-145">Menu button</span></span>
* <span data-ttu-id="0d22c-146">グリップボタン</span><span class="sxs-lookup"><span data-stu-id="0d22c-146">Grip button</span></span>
* <span data-ttu-id="0d22c-147">Touchpad</span><span class="sxs-lookup"><span data-stu-id="0d22c-147">Touchpad</span></span>
* <span data-ttu-id="0d22c-148">スティック</span><span class="sxs-lookup"><span data-stu-id="0d22c-148">Thumbstick</span></span>
* <span data-ttu-id="0d22c-149">バッテリレベル</span><span class="sxs-lookup"><span data-stu-id="0d22c-149">Battery level</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0d22c-150">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="0d22c-150">Next Development Checkpoint</span></span>

<span data-ttu-id="0d22c-151">私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は配置段階にいます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-151">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="0d22c-152">ここからは、次の [トピック](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) に進むことも、高度なサービスの追加に直接移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d22c-152">From here, you can continue to the next [topic](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) or jump directly to adding advanced services.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d22c-153">高度なサービス</span><span class="sxs-lookup"><span data-stu-id="0d22c-153">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a><span data-ttu-id="0d22c-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d22c-154">See also</span></span>
* [<span data-ttu-id="0d22c-155">HoloLens エミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="0d22c-155">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="0d22c-156">高度な Mixed Reality シミュレーター入力</span><span class="sxs-lookup"><span data-stu-id="0d22c-156">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="0d22c-157">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0d22c-157">Spatial mapping in Unity</span></span>](../../develop/unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="0d22c-158">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0d22c-158">Spatial mapping in DirectX</span></span>](../../develop/native/spatial-mapping-in-directx.md)
