---
title: モーション コントローラー
description: アプリケーションで Mixed Reality モーションコントローラーを使用した入力相互作用を設定する方法について説明します。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof コントローラー、モーションコントローラー、ペアリング、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット、HoloLens、スクロール、グリップ、状態
ms.openlocfilehash: 94a9292b3a765131ae197fd9f91c27a52a463eef
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192620"
---
# <a name="motion-controllers"></a><span data-ttu-id="75618-104">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="75618-104">Motion controllers</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="75618-105">モーションコントローラーは、ユーザーが mixed reality でアクションを実行できるようにする [ハードウェアアクセサリ](../discover/hardware-accessories.md) です。</span><span class="sxs-lookup"><span data-stu-id="75618-105">Motion controllers are [hardware accessories](../discover/hardware-accessories.md) that allow users to take action in mixed reality.</span></span> <span data-ttu-id="75618-106">[ジェスチャ](gaze-and-commit.md#composite-gestures)を使用したモーションコントローラーの利点は、コントローラーが領域内に正確な位置を持ち、デジタルオブジェクトと詳細に対話できることです。</span><span class="sxs-lookup"><span data-stu-id="75618-106">An advantage of motion controllers over [gestures](gaze-and-commit.md#composite-gestures) is that the controllers have a precise position in space, allowing for fine grained interaction with digital objects.</span></span> <span data-ttu-id="75618-107">Windows Mixed Reality イマーシブヘッドセットの場合、モーションコントローラーは、ユーザーが世界中でアクションを実行する主な方法です。</span><span class="sxs-lookup"><span data-stu-id="75618-107">For Windows Mixed Reality immersive headsets, motion controllers are the primary way that users will take action in their world.</span></span><br>
        <br>
        <span data-ttu-id="75618-108">*イメージ: Windows Mixed Reality モーションコントローラー*</span><span class="sxs-lookup"><span data-stu-id="75618-108">*Image: A Windows Mixed Reality motion controller*</span></span>
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality モーションコントローラー](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a><span data-ttu-id="75618-110">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="75618-110">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="75618-111"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="75618-111"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="75618-112"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="75618-112"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="75618-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="75618-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="75618-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="75618-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="75618-115">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="75618-115">Motion controllers</span></span></td>
     <td>❌</td>
     <td>❌</td>
     <td><span data-ttu-id="75618-116">✔️</span><span class="sxs-lookup"><span data-stu-id="75618-116">✔️</span></span></td>
</tr>
</table>

## <a name="hardware-details"></a><span data-ttu-id="75618-117">ハードウェアの詳細</span><span class="sxs-lookup"><span data-stu-id="75618-117">Hardware details</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="75618-118">Windows Mixed Reality モーションコントローラーは、イマーシブヘッドセットのセンサーを使用して、ビューのフィールドで正確で応答性の高い移動追跡を提供します。</span><span class="sxs-lookup"><span data-stu-id="75618-118">Windows Mixed Reality motion controllers offer precise and responsive movement tracking in your field of view using the sensors in the immersive headset.</span></span> <span data-ttu-id="75618-119">領域の壁にハードウェアを取り付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="75618-119">There's no need to install hardware on the walls in your space.</span></span> <span data-ttu-id="75618-120">これらのモーションコントローラーは、Windows Mixed Reality のイマーシブヘッドセットと同じように簡単なセットアップと移植性を提供します。</span><span class="sxs-lookup"><span data-stu-id="75618-120">These motion controllers will offer the same ease of setup and portability as Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="75618-121">デバイスパートナーは、この休日を利用して、これらのコントローラーを小売店で販売し、販売する予定です。</span><span class="sxs-lookup"><span data-stu-id="75618-121">Our device partners plan to market and sell these controllers on retail shelves this holiday.</span></span>

<span data-ttu-id="75618-122">![コントローラーを知る](images/controllerimage-750px.png)</span><span class="sxs-lookup"><span data-stu-id="75618-122">![Get to know your controller](images/controllerimage-750px.png)</span></span><br>
<span data-ttu-id="75618-123">*コントローラーを知る*</span><span class="sxs-lookup"><span data-stu-id="75618-123">*Get to know your controller*</span></span>

<span data-ttu-id="75618-124">**機能:**</span><span class="sxs-lookup"><span data-stu-id="75618-124">**Features:**</span></span>
* <span data-ttu-id="75618-125">光学式の追跡</span><span class="sxs-lookup"><span data-stu-id="75618-125">Optical tracking</span></span>
* <span data-ttu-id="75618-126">トリガー</span><span class="sxs-lookup"><span data-stu-id="75618-126">Trigger</span></span>
* <span data-ttu-id="75618-127">グラブボタン</span><span class="sxs-lookup"><span data-stu-id="75618-127">Grab button</span></span>
* <span data-ttu-id="75618-128">スティック</span><span class="sxs-lookup"><span data-stu-id="75618-128">Thumbstick</span></span>
* <span data-ttu-id="75618-129">Touchpad</span><span class="sxs-lookup"><span data-stu-id="75618-129">Touchpad</span></span>

## <a name="setup"></a><span data-ttu-id="75618-130">セットアップ</span><span class="sxs-lookup"><span data-stu-id="75618-130">Setup</span></span>

### <a name="before-you-begin"></a><span data-ttu-id="75618-131">開始する前に</span><span class="sxs-lookup"><span data-stu-id="75618-131">Before you begin</span></span>

<span data-ttu-id="75618-132">**要件:**</span><span class="sxs-lookup"><span data-stu-id="75618-132">**You'll need:**</span></span>
* <span data-ttu-id="75618-133">2つのモーションコントローラーのセット。</span><span class="sxs-lookup"><span data-stu-id="75618-133">A set of two motion controllers.</span></span>
* <span data-ttu-id="75618-134">4つの AA バッテリ。</span><span class="sxs-lookup"><span data-stu-id="75618-134">Four AA batteries.</span></span>
* <span data-ttu-id="75618-135">Bluetooth 4.0 がサポートされている PC。</span><span class="sxs-lookup"><span data-stu-id="75618-135">A PC with Bluetooth 4.0 support.</span></span>

<span data-ttu-id="75618-136">**Windows、Unity、ドライバーの更新プログラムを確認する**</span><span class="sxs-lookup"><span data-stu-id="75618-136">**Check for Windows, Unity, and driver updates**</span></span>
* <span data-ttu-id="75618-137">Mixed reality 開発については、「Windows、Unity、およびその他のバージョン用の [ツールをインストール](../develop/install-the-tools.md) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75618-137">Visit [Install the tools](../develop/install-the-tools.md) for the preferred versions of Windows, Unity, and so on, for mixed reality development.</span></span>
* <span data-ttu-id="75618-138">最新の [ヘッドセットとモーションコントローラードライバー](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="75618-138">Make sure you have the most up-to-date [headset and motion controller drivers](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).</span></span>

### <a name="pairing-controllers"></a><span data-ttu-id="75618-139">コントローラーのペアリング</span><span class="sxs-lookup"><span data-stu-id="75618-139">Pairing controllers</span></span>

<span data-ttu-id="75618-140">モーションコントローラーは、他の Bluetooth デバイスと同様に、Windows 設定を使用してホスト PC と結合できます。</span><span class="sxs-lookup"><span data-stu-id="75618-140">Motion controllers can be bonded with host PC using Windows settings like any other Bluetooth device.</span></span>

1. <span data-ttu-id="75618-141">2つの AA バッテリをコントローラーの背面に挿入します。</span><span class="sxs-lookup"><span data-stu-id="75618-141">Insert two AA batteries into the back of the controller.</span></span> <span data-ttu-id="75618-142">ここではバッテリカバーをオフのままにします。</span><span class="sxs-lookup"><span data-stu-id="75618-142">Leave the battery cover off for now.</span></span>
2. <span data-ttu-id="75618-143">組み込みの Bluetooth ラジオではなく外部 USB Bluetooth アダプターを使用している場合は、先に進む前に、 [bluetooth のベストプラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="75618-143">If you're using an external USB Bluetooth Adapter instead of a built-in Bluetooth radio, review the [Bluetooth best practices](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) before proceeding.</span></span> <span data-ttu-id="75618-144">組み込みのラジオを使用したデスクトップ構成の場合は、アンテナが接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="75618-144">For desktop configuration with built-in radio, ensure antenna is connected.</span></span>
3. <span data-ttu-id="75618-145">[ **Windows 設定**  ->  ] [**デバイス**  ->  ] を開き、**bluetooth またはその他のデバイス**  ->  **bluetooth** を追加し、以前の "motion controller – Right" と "motion controller – Left" のインスタンスをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="75618-145">Open **Windows Settings** -> **Devices** -> **Add Bluetooth or other device** -> **Bluetooth** and remove any earlier instances of “Motion controller – Right” and “Motion controller – Left”.</span></span> <span data-ttu-id="75618-146">一覧の下部にある [その他のデバイス] カテゴリも確認します。</span><span class="sxs-lookup"><span data-stu-id="75618-146">Check also Other devices category at the bottom of the list.</span></span>
4. <span data-ttu-id="75618-147">[ **Bluetooth またはその他のデバイスの追加** ] を選択すると、bluetooth デバイスの検出が開始されます。</span><span class="sxs-lookup"><span data-stu-id="75618-147">Select **Add Bluetooth or other device** and see it starting to discover Bluetooth devices.</span></span>
5. <span data-ttu-id="75618-148">コントローラーの [Windows] ボタンを押してコントローラーをオンにすると、buzzes すると解放されます。</span><span class="sxs-lookup"><span data-stu-id="75618-148">Press and hold the controller's Windows button to turn on the controller, release once it buzzes.</span></span>
6. <span data-ttu-id="75618-149">Led の発するが開始されるまで、ペアリングボタン (バッテリコンパートメントのタブ) を押したままにします。</span><span class="sxs-lookup"><span data-stu-id="75618-149">Press and hold the pairing button (tab in the battery compartment) until the LEDs begin pulsing.</span></span>

:::row:::
    :::column:::
7. <span data-ttu-id="75618-150">リストの一番下に "Motion controller-Left" または "Motion controller-Right" が表示されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="75618-150">Wait "Motion controller - Left" or "Motion controller - Right" to appear to the bottom of the list.</span></span> <span data-ttu-id="75618-151">ペアにする場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="75618-151">Select to pair.</span></span> <span data-ttu-id="75618-152">接続されると、コントローラーは1回バイブレーションされます。</span><span class="sxs-lookup"><span data-stu-id="75618-152">Controller will vibrate once when connected.</span></span><br>
        <br>
        <span data-ttu-id="75618-153">*イメージ: ペアにする "モーションコントローラー" を選択します。複数のインスタンスがある場合は、一覧の一番下から1つを選択します。*</span><span class="sxs-lookup"><span data-stu-id="75618-153">*Image: Select "Motion controller" to pair; if there are multiple instances, select one from the bottom of the list*</span></span>
    :::column-end:::
        :::column:::
       ![ペアにするモーションコントローラーを選択します。複数のインスタンスがある場合は、一覧の下部に表示されます。](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. <span data-ttu-id="75618-155">[**マウス、キーボード、& ペン] カテゴリ** の [Bluetooth 設定] にコントローラーが **表示されます。**</span><span class="sxs-lookup"><span data-stu-id="75618-155">You'll see the controller appear in the Bluetooth settings under **“Mouse, keyboard, & pen” category** as **Connected**.</span></span> <span data-ttu-id="75618-156">この時点で、ファームウェアの更新プログラムを入手できます。 [次のセクション](motion-controllers.md#updating-controller-firmware)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75618-156">At this point, you may get a firmware update – see [next section](motion-controllers.md#updating-controller-firmware).</span></span>
9. <span data-ttu-id="75618-157">バッテリカバーを再接続します。</span><span class="sxs-lookup"><span data-stu-id="75618-157">Reattach battery cover.</span></span>
10. <span data-ttu-id="75618-158">2番目のコントローラーに対して手順1-9 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="75618-158">Repeat steps 1-9 for the second controller.</span></span>

<br>

:::row:::
    :::column:::
        <span data-ttu-id="75618-159">両方のコントローラーが正常にペアリングされると、設定は次のようになります。 [**マウス、キーボード、& ペン] カテゴリ** の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="75618-159">After successfully pairing both controllers, your settings should look like the following, under **“Mouse, keyboard, & pen” category**</span></span> <br>
        <br>
        <span data-ttu-id="75618-160">*画像: モーションコントローラーが接続されました*</span><span class="sxs-lookup"><span data-stu-id="75618-160">*Image: Motion controllers connected*</span></span>
    :::column-end:::
        :::column:::
       ![接続コントローラー](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

<span data-ttu-id="75618-162">ペアリング後にコントローラーがオフになっている場合、それらの状態はペアとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="75618-162">If the controllers are turned off after pairing, their status will show up as Paired.</span></span> <span data-ttu-id="75618-163">[その他のデバイス] カテゴリの下にあるコントローラーの場合、ペアリングが部分的にしか完了していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75618-163">For controllers permanently under the “Other devices” category, pairing may have only partially completed.</span></span> <span data-ttu-id="75618-164">この場合は、ペアリング手順を再度実行して、コントローラーを機能させることができます。</span><span class="sxs-lookup"><span data-stu-id="75618-164">In this case, run the pairing steps again to get controller functional.</span></span>

### <a name="updating-controller-firmware"></a><span data-ttu-id="75618-165">コントローラーのファームウェアを更新しています</span><span class="sxs-lookup"><span data-stu-id="75618-165">Updating controller firmware</span></span>

* <span data-ttu-id="75618-166">新しいコントローラーファームウェアを使用して、イマーシブヘッドセットが PC に接続されている場合は、次に電源をオンにしたときに、そのファームウェアが自動的にモーションコントローラーにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="75618-166">If an immersive headset is connected to your PC with new controller firmware is available, the firmware will be pushed to your motion controllers automatically the next time you turn them on.</span></span> <span data-ttu-id="75618-167">コントローラーファームウェアの更新プログラムは、円形の動きにおける LED のある領域を照明するパターンによって示され、1-2 分かかります。</span><span class="sxs-lookup"><span data-stu-id="75618-167">Controller firmware updates are indicated by a pattern of illuminating LED quadrants in a circular motion, and take 1-2 minutes.</span></span>


:::row:::
    :::column:::
* <span data-ttu-id="75618-168">ファームウェアの更新が完了すると、コントローラーが再起動して再接続されます。</span><span class="sxs-lookup"><span data-stu-id="75618-168">After the firmware update completes, the controllers will reboot and reconnect.</span></span> <span data-ttu-id="75618-169">両方のコントローラーがすぐに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="75618-169">Both controllers should be connected now.</span></span> <br>
        <br>
        <span data-ttu-id="75618-170">*イメージ: Bluetooth 設定で接続されているコントローラー*</span><span class="sxs-lookup"><span data-stu-id="75618-170">*Image: Controllers connected in Bluetooth settings*</span></span>
    :::column-end:::
        :::column:::
       ![接続されたコントローラー](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* <span data-ttu-id="75618-172">コントローラーが正常に動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="75618-172">Verify your controllers work properly:</span></span>
    1. <span data-ttu-id="75618-173">**Mixed Reality ポータル** を起動し、Mixed reality ホームを入力します。</span><span class="sxs-lookup"><span data-stu-id="75618-173">Launch **Mixed Reality Portal** and enter your Mixed Reality Home.</span></span>
    2. <span data-ttu-id="75618-174">コントローラーを移動し、追跡、テストボタンを確認して、 [テレ](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) を確認します。</span><span class="sxs-lookup"><span data-stu-id="75618-174">Move your controllers and verify tracking, test buttons, and verify [teleportation](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) works.</span></span> <span data-ttu-id="75618-175">そうでない場合は、「 [モーションコントローラーのトラブルシューティング](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75618-175">If they don't, then check out [motion controller troubleshooting](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).</span></span>

## <a name="gazing-and-pointing"></a><span data-ttu-id="75618-176">ガスとポイント</span><span class="sxs-lookup"><span data-stu-id="75618-176">Gazing and pointing</span></span>

<span data-ttu-id="75618-177">Windows Mixed Reality では、対話のために2つの主要なモデルがサポートされます。 **宝石を見つめ、コミット** して、 **ポイントアンドコミット** します。</span><span class="sxs-lookup"><span data-stu-id="75618-177">Windows Mixed Reality supports two key models for interaction; **gaze and commit** and **point and commit**:</span></span>
* <span data-ttu-id="75618-178">ユーザーは、 **宝石とコミット** を使用して、 [宝石](gaze-and-commit.md)を持つオブジェクトを対象にして、ハンドタップ、ゲームパッド、clicker、または音声を使用してオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="75618-178">With **gaze and commit**, users target an object with their [gaze](gaze-and-commit.md), and then select objects with hand air-taps, a gamepad, a clicker, or their voice.</span></span>
* <span data-ttu-id="75618-179">**ポイントとコミット** を使用すると、ユーザーは、ポイント対応のモーションコントローラーをターゲットオブジェクトでターゲットにして、コントローラーのトリガーを持つオブジェクトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="75618-179">With **point and commit**, a user can aim a pointing-capable motion controller at the target object and then select objects with the controller's trigger.</span></span>

<span data-ttu-id="75618-180">また、モーションコントローラーを使用したポイントをサポートするアプリでは、可能な場合は、ユーザーが使用する入力デバイスにユーザーが選択できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="75618-180">Apps that support pointing with motion controllers should also enable gaze-driven interactions where possible, to give users a choice in what input devices they use.</span></span>

### <a name="managing-recoil-when-pointing"></a><span data-ttu-id="75618-181">ポイント時の recoil の管理</span><span class="sxs-lookup"><span data-stu-id="75618-181">Managing recoil when pointing</span></span>

<span data-ttu-id="75618-182">モーションコントローラーを使用してポイントアンドコミットする場合、ユーザーはコントローラーを使用して、そのトリガーをプルすることによってターゲットを指定し、対話します。</span><span class="sxs-lookup"><span data-stu-id="75618-182">When using motion controllers to point and commit, your users will use the controller to target and interact by pulling its trigger.</span></span> <span data-ttu-id="75618-183">トリガーの vigorously を取得したユーザーは、意図したものよりも、トリガーをプルした時点よりも先にコントローラーの位置を上げる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75618-183">Users who pull the trigger vigorously may end up aiming the controller higher at the end of their trigger pull than they'd intended.</span></span>

<span data-ttu-id="75618-184">ユーザーがトリガーをプルしたときに発生する可能性のある recoil を管理するために、トリガーのアナログ軸の値が0.0 を超えたときに、アプリでターゲットの射線をスナップできます。</span><span class="sxs-lookup"><span data-stu-id="75618-184">To manage any such recoil that may occur when users pull the trigger, your app can snap its targeting ray when the trigger's analog axis value rises above 0.0.</span></span> <span data-ttu-id="75618-185">その後、最後の押しが短い時間枠で実行される限り、後で、トリガー値が1.0 になると、そのターゲットを使用してアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="75618-185">You can then take action using that targeting ray a few frames later once the trigger value reaches 1.0, as long as the final press occurs within a short time window.</span></span> <span data-ttu-id="75618-186">高レベルの [複合タップジェスチャ](gaze-and-commit.md#composite-gestures)を使用すると、このターゲット設定を制御することになります。</span><span class="sxs-lookup"><span data-stu-id="75618-186">When using the higher-level [composite Tap gesture](gaze-and-commit.md#composite-gestures), Windows will manage this targeting ray capture and timeout for you.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="75618-187">グリップポーズとポインティングポーズ</span><span class="sxs-lookup"><span data-stu-id="75618-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="75618-188">Windows Mixed Reality では、さまざまなフォームファクターのモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。</span><span class="sxs-lookup"><span data-stu-id="75618-188">Windows Mixed Reality supports motion controllers in different form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="75618-189">これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。 **グリップ** と **ポインター** があります。</span><span class="sxs-lookup"><span data-stu-id="75618-189">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source; the **grip pose** and the **pointer pose**.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="75618-190">グリップの原因</span><span class="sxs-lookup"><span data-stu-id="75618-190">Grip pose</span></span>

<span data-ttu-id="75618-191">**グリップ** は、HoloLens によって検出された、または運動コントローラーを持つパームのいずれかの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="75618-191">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="75618-192">イマーシブヘッドセットでは、グリップは、 **ユーザーの手** や、剣や銃など、 **ユーザーの手に保持** されているオブジェクトをレンダリングするために最適です。</span><span class="sxs-lookup"><span data-stu-id="75618-192">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="75618-193">また、このグリップは、モーションコントローラーを視覚化するときにも使用されます。これは、モーションコントローラー用に Windows によって提供される **描画モデル** が、グリップを原点と回転の中心として使用するためです。</span><span class="sxs-lookup"><span data-stu-id="75618-193">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="75618-194">グリップは、次のように明確に定義されます。</span><span class="sxs-lookup"><span data-stu-id="75618-194">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="75618-195">**グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。</span><span class="sxs-lookup"><span data-stu-id="75618-195">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="75618-196">Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。</span><span class="sxs-lookup"><span data-stu-id="75618-196">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="75618-197">**グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、</span><span class="sxs-lookup"><span data-stu-id="75618-197">The **grip orientation's Right axis**: When you completely open your hand to form a flat five-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="75618-198">**グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。</span><span class="sxs-lookup"><span data-stu-id="75618-198">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="75618-199">**グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。</span><span class="sxs-lookup"><span data-stu-id="75618-199">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="75618-200">ポインターのポーズ</span><span class="sxs-lookup"><span data-stu-id="75618-200">Pointer pose</span></span>

<span data-ttu-id="75618-201">**ポインター** は、前方にあるコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="75618-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="75618-202">システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="75618-202">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="75618-203">仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、その仮想オブジェクトの最も自然な射線をポイントする必要があります (アプリ定義の銃モデルの胴体に沿って移動する射線など)。</span><span class="sxs-lookup"><span data-stu-id="75618-203">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="75618-204">ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。</span><span class="sxs-lookup"><span data-stu-id="75618-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="75618-205">コントローラー追跡状態</span><span class="sxs-lookup"><span data-stu-id="75618-205">Controller tracking state</span></span>

<span data-ttu-id="75618-206">ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="75618-206">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="75618-207">代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。</span><span class="sxs-lookup"><span data-stu-id="75618-207">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="75618-208">ユーザーがヘッドセットのビューのフィールドからコントローラーを移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測してアプリに提供し続けます。</span><span class="sxs-lookup"><span data-stu-id="75618-208">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="75618-209">コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="75618-209">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="75618-210">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="75618-210">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="75618-211">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かなくても、おおよその精度で正常に動作できます。</span><span class="sxs-lookup"><span data-stu-id="75618-211">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="75618-212">状態の明示的な追跡に関する推論</span><span class="sxs-lookup"><span data-stu-id="75618-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="75618-213">追跡の状態に基づいて位置を異なる方法で処理する必要があるアプリは、さらに詳細になり、コントローラーの状態 (SourceLossRisk や PositionAccuracy など) のプロパティを検査することができます。</span><span class="sxs-lookup"><span data-stu-id="75618-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as SourceLossRisk and PositionAccuracy:</span></span>

<table>
<tr>
<th> <span data-ttu-id="75618-214">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="75618-214">Tracking state</span></span> </th><th> <span data-ttu-id="75618-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="75618-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="75618-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="75618-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="75618-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="75618-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="75618-218"><b>高精度</b> </span><span class="sxs-lookup"><span data-stu-id="75618-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="75618-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="75618-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="75618-220">高</span><span class="sxs-lookup"><span data-stu-id="75618-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="75618-221">true</span><span class="sxs-lookup"><span data-stu-id="75618-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75618-222"><b>高精度 (消失のリスク)</b> </span><span class="sxs-lookup"><span data-stu-id="75618-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="75618-223">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="75618-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="75618-224">高</span><span class="sxs-lookup"><span data-stu-id="75618-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="75618-225">true</span><span class="sxs-lookup"><span data-stu-id="75618-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75618-226"><b>おおよその精度</b> </span><span class="sxs-lookup"><span data-stu-id="75618-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="75618-227">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="75618-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="75618-228">Approximate</span><span class="sxs-lookup"><span data-stu-id="75618-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="75618-229">true</span><span class="sxs-lookup"><span data-stu-id="75618-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="75618-230"><b>位置なし</b> </span><span class="sxs-lookup"><span data-stu-id="75618-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="75618-231">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="75618-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="75618-232">Approximate</span><span class="sxs-lookup"><span data-stu-id="75618-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="75618-233">false</span><span class="sxs-lookup"><span data-stu-id="75618-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="75618-234">これらのモーションコントローラーの追跡状態は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="75618-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="75618-235">**高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。</span><span class="sxs-lookup"><span data-stu-id="75618-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="75618-236">一時的にビューのフィールドから離れるか、ヘッドセットセンサーから瞬間的に見えなくなっている移動コントローラー (たとえば、ユーザーによる) は、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを引き続き返します。</span><span class="sxs-lookup"><span data-stu-id="75618-236">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (for example, by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="75618-237">**高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。</span><span class="sxs-lookup"><span data-stu-id="75618-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="75618-238">アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。</span><span class="sxs-lookup"><span data-stu-id="75618-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="75618-239">その時点で、アプリは、高い品質を備えた安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="75618-239">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="75618-240">**おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="75618-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="75618-241">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="75618-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="75618-242">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。</span><span class="sxs-lookup"><span data-stu-id="75618-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="75618-243">入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します**。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。</span><span class="sxs-lookup"><span data-stu-id="75618-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="75618-244">**位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされた位置であっても、その時点では意味がないことをシステムが認識している場合があります。</span><span class="sxs-lookup"><span data-stu-id="75618-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="75618-245">たとえば、電源がオンにされたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。</span><span class="sxs-lookup"><span data-stu-id="75618-245">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="75618-246">これらのタイミングでは、システムはアプリに位置を提供せず、 **TryGetPosition** は false を返します。</span><span class="sxs-lookup"><span data-stu-id="75618-246">At those times, the system won't provide any position to the app, and **TryGetPosition** will return false.</span></span>

## <a name="interactions-low-level-spatial-input"></a><span data-ttu-id="75618-247">相互作用: 低レベルの空間入力</span><span class="sxs-lookup"><span data-stu-id="75618-247">Interactions: Low-level spatial input</span></span>

<span data-ttu-id="75618-248">ハンズオンコントローラーとモーションコントローラーの間の主要な相互作用は、 **選択**、 **メニュー**、 **つかみ**、 **タッチパッド**、 **サムスティック**、および **ホーム** です。</span><span class="sxs-lookup"><span data-stu-id="75618-248">The core interactions across hands and motion controllers are **Select**, **Menu**, **Grasp**, **Touchpad**, **Thumbstick**, and **Home**.</span></span>
* <span data-ttu-id="75618-249">**選択** は、ホログラムをアクティブにするための主要な相互作用です。これは、プレスとその後のリリースで構成されます。</span><span class="sxs-lookup"><span data-stu-id="75618-249">**Select** is the primary interaction to activate a hologram, consisting of a press followed by a release.</span></span> <span data-ttu-id="75618-250">モーションコントローラーの場合は、コントローラーのトリガーを使用して、選択したプレスを実行します。</span><span class="sxs-lookup"><span data-stu-id="75618-250">For motion controllers, you perform a Select press using the controller's trigger.</span></span> <span data-ttu-id="75618-251">選択を実行する他の方法として、 [音声コマンド](voice-input.md) "Select" を読み上げます。</span><span class="sxs-lookup"><span data-stu-id="75618-251">Other ways to perform a Select are by speaking the [voice command](voice-input.md) "Select".</span></span> <span data-ttu-id="75618-252">同じ選択操作を任意のアプリ内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="75618-252">The same select interaction can be used within any app.</span></span> <span data-ttu-id="75618-253">Select は、マウスのクリックと同等のものと考えることができます。1回学習してからすべてのアプリに適用する、ユニバーサルアクション。</span><span class="sxs-lookup"><span data-stu-id="75618-253">Think of Select as the equivalent of a mouse click; a universal action that you learn once and then apply across all your apps.</span></span>
* <span data-ttu-id="75618-254">**メニュー** は、オブジェクトを操作するための二次的な相互作用であり、コンテキストメニューを取得したり、他のセカンダリアクションを実行したりするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="75618-254">**Menu** is the secondary interaction for acting on an object, used to pull up a context menu or take some other secondary action.</span></span> <span data-ttu-id="75618-255">モーションコントローラーを使用すると、コントローラーの *メニュー* ボタンを使用してメニュー操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="75618-255">With motion controllers, you can take a menu action using the controller's *menu* button.</span></span> <span data-ttu-id="75618-256">(つまり、ハンバーガー "menu" アイコンが付いたボタン)</span><span class="sxs-lookup"><span data-stu-id="75618-256">(that is, the button with the hamburger "menu" icon on it)</span></span>
* <span data-ttu-id="75618-257">**理解** することは、ユーザーが直接オブジェクトを操作して操作できるようにする方法です。</span><span class="sxs-lookup"><span data-stu-id="75618-257">**Grasp** is how users can directly take action on objects at their hand to manipulate them.</span></span> <span data-ttu-id="75618-258">モーションコントローラーを使用すると、最初に厳密につかんで操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="75618-258">With motion controllers, you can do a grasp action by squeezing your fist tightly.</span></span> <span data-ttu-id="75618-259">モーションコントローラーは、グラブボタン、パームトリガー、またはその他のセンサーを使用して、つかみを検出する場合があります。</span><span class="sxs-lookup"><span data-stu-id="75618-259">A motion controller may detect a Grasp with a grab button, palm trigger, or other sensor.</span></span>
* <span data-ttu-id="75618-260">**タッチパッド** を使用すると、ユーザーは、モーションコントローラーのタッチパッドの表面に沿って2つのディメンションのアクションを調整し、タッチパッドの [下へ] をクリックしてアクションをコミットできます。</span><span class="sxs-lookup"><span data-stu-id="75618-260">**Touchpad** allows the user to adjust an action in two dimensions along the surface of a motion controller's touchpad, committing the action by clicking down on the touchpad.</span></span> <span data-ttu-id="75618-261">タッチパッド向けは、押された状態、タッチされた状態、および正規化された XY 座標を提供します。</span><span class="sxs-lookup"><span data-stu-id="75618-261">Touchpads provide a pressed state, touched state, and normalized XY coordinates.</span></span> <span data-ttu-id="75618-262">X と Y の範囲は、円形のタッチパッドの範囲で、中央は (0, 0) です。</span><span class="sxs-lookup"><span data-stu-id="75618-262">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="75618-263">X の場合、-1 は左に、1は右側にあります。</span><span class="sxs-lookup"><span data-stu-id="75618-263">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="75618-264">Y の場合、-1 が一番下にあり、1が一番上にあります。</span><span class="sxs-lookup"><span data-stu-id="75618-264">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="75618-265">**サムスティック** を使用すると、ユーザーは、モーションコントローラーのサムスティックを円形の範囲内に移動することで、2つのディメンションのアクションを調整できます。これにより、サムスティック上で [下へ] をクリックしてアクションをコミットできます。</span><span class="sxs-lookup"><span data-stu-id="75618-265">**Thumbstick** allows the user to adjust an action in two dimensions by moving a motion controller's thumbstick within its circular range, committing the action by clicking down on the thumbstick.</span></span> <span data-ttu-id="75618-266">Thumbsticks は、押された状態と正規化された XY 座標も提供します。</span><span class="sxs-lookup"><span data-stu-id="75618-266">Thumbsticks also provide a pressed state and normalized XY coordinates.</span></span> <span data-ttu-id="75618-267">X と Y の範囲は、円形のタッチパッドの範囲で、中央は (0, 0) です。</span><span class="sxs-lookup"><span data-stu-id="75618-267">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="75618-268">X の場合、-1 は左に、1は右側にあります。</span><span class="sxs-lookup"><span data-stu-id="75618-268">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="75618-269">Y の場合、-1 が一番下にあり、1が一番上にあります。</span><span class="sxs-lookup"><span data-stu-id="75618-269">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="75618-270">**Home** は、[スタート] メニューに戻るために使用される特殊なシステムアクションです。</span><span class="sxs-lookup"><span data-stu-id="75618-270">**Home** is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="75618-271">これは、キーボードで Windows キーを押すか、Xbox コントローラーの Xbox ボタンを押すのと似ています。</span><span class="sxs-lookup"><span data-stu-id="75618-271">It's similar to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="75618-272">モーションコントローラーの Windows ボタンを押すと、ホームに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="75618-272">You can go Home by pressing the Windows button on a motion controller.</span></span> <span data-ttu-id="75618-273">まず、"Cortana, 帰宅してください" と言うと、いつでも開始できます。</span><span class="sxs-lookup"><span data-stu-id="75618-273">Note, you can always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="75618-274">アプリは、システムによって処理されるため、特にホームアクションに対応することはできません。</span><span class="sxs-lookup"><span data-stu-id="75618-274">Apps can't react specifically to Home actions, as these are handled by the system.</span></span>

## <a name="composite-gestures-high-level-spatial-input"></a><span data-ttu-id="75618-275">複合ジェスチャ: 高度な空間入力</span><span class="sxs-lookup"><span data-stu-id="75618-275">Composite gestures: High-level spatial input</span></span>

<span data-ttu-id="75618-276">[ハンドジェスチャ](gaze-and-commit.md#composite-gestures)とモーションコントローラーはどちらも、高レベルの **[複合ジェスチャ](gaze-and-commit.md#composite-gestures)** の共通セットを検出するために、時間の経過と共に追跡できます。</span><span class="sxs-lookup"><span data-stu-id="75618-276">Both [hand gestures](gaze-and-commit.md#composite-gestures) and motion controllers can be tracked over time to detect a common set of high-level **[composite gestures](gaze-and-commit.md#composite-gestures)**.</span></span> <span data-ttu-id="75618-277">これにより、アプリは、ユーザーがハンドまたはコントローラーを使用するかどうかにかかわらず、高レベルの **タップ**、 **保持**、 **操作** 、および **ナビゲーション** ジェスチャを検出できます。</span><span class="sxs-lookup"><span data-stu-id="75618-277">This enables your app to detect high-level **tap**, **hold**, **manipulation** and **navigation** gestures, whether users end up using hands or controllers.</span></span>

## <a name="rendering-the-motion-controller-model"></a><span data-ttu-id="75618-278">モーションコントローラーモデルのレンダリング</span><span class="sxs-lookup"><span data-stu-id="75618-278">Rendering the motion controller model</span></span>

<span data-ttu-id="75618-279">**3d コントローラーモデル** Windows は、システムで現在アクティブになっている各モーションコントローラーの描画モデルをアプリで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="75618-279">**3D controller models** Windows makes available to apps a renderable model of each motion controller currently active in the system.</span></span> <span data-ttu-id="75618-280">アプリケーションが実行時にこれらのシステム提供のコントローラーモデルを動的に読み込んで明確にすることにより、アプリが将来のコントローラー設計に確実に上位互換性を持つようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="75618-280">By having your app dynamically load and articulate these system-provided controller models at runtime, you can ensure your app is forward-compatible to any future controller designs.</span></span>

<span data-ttu-id="75618-281">モデルの原点が物理的な世界のこの点に合わせているため、コントローラーの **グリップ** ですべての描画モデルをレンダリングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="75618-281">We recommend rendering all renderable models at the **grip pose** of the controller, as the origin of the model is aligned with this point in the physical world.</span></span> <span data-ttu-id="75618-282">コントローラーモデルをレンダリングしている場合は、コントローラーの物理的な設計に基づいて、ユーザーが自然に指している光線を表す、 **ポインター** の raycast からシーンを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="75618-282">If you're rendering controller models, you may then wish to raycast into your scene from the **pointer pose**, which represents the ray along which users will naturally expect to point, given that controller's physical design.</span></span>

<span data-ttu-id="75618-283">Unity でコントローラーモデルを動的に読み込む方法の詳細については、「 [unity でのモーションコントローラーモデルのレンダリング](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75618-283">For more information about how to load controller models dynamically in Unity, see the [Rendering the motion controller model in Unity](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) section.</span></span>

<span data-ttu-id="75618-284">**2d コントローラーのラインアート** App controller のヒントとコマンドを app controller モデル自体にアタッチすることをお勧めしますが、開発者によっては、単純な "チュートリアル" または "操作方法" の UI で、モーションコントローラーの2D ラインアート表現を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="75618-284">**2D controller line art** While we recommend attaching in-app controller tips and commands to the in-app controller models themselves, some developers may want to use 2D line art representations of the motion controllers in flat "tutorial" or "how-to" UI.</span></span> <span data-ttu-id="75618-285">これらの開発者にとっては、次の黒と白の両方で、.png のモーションコントローラーのラインアートファイルを使用できるようにしました (右クリックして保存します)。</span><span class="sxs-lookup"><span data-stu-id="75618-285">For those developers, we've made .png motion controller line art files available in both black and white below (right-click to save).</span></span>

![モーションコントローラーのラインアートのプレビュー](images/motioncontrollers-black-preview-300px.png)

[<span data-ttu-id="75618-287">' ' ' 白 ' ' ' の完全解像度のモーションコントローラーのラインアート</span><span class="sxs-lookup"><span data-stu-id="75618-287">Full-resolution motion controllers line art in '''white'''</span></span>](images/motioncontrollers-white.png)
 
[<span data-ttu-id="75618-288">' ' ' Black ' ' ' の完全解像度のモーションコントローラーのラインアート</span><span class="sxs-lookup"><span data-stu-id="75618-288">Full-resolution motion controllers line art in '''black'''</span></span>](images/motioncontrollers-black.png)

## <a name="faq"></a><span data-ttu-id="75618-289">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="75618-289">FAQ</span></span>

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a><span data-ttu-id="75618-290">複数の Pc にモーションコントローラーを組み合わせることはできますか。</span><span class="sxs-lookup"><span data-stu-id="75618-290">Can I pair motion controllers to multiple PCs?</span></span>

<span data-ttu-id="75618-291">モーションコントローラーは、1台の PC とのペアリングをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="75618-291">Motion controllers support pairing with a single PC.</span></span> <span data-ttu-id="75618-292">[モーションコントローラーのセットアップ](motion-controllers.md#setup)の指示に従って、コントローラーをペアリングします。</span><span class="sxs-lookup"><span data-stu-id="75618-292">Follow instructions on [motion controller setup](motion-controllers.md#setup) to pair your controllers.</span></span>

### <a name="how-do-i-update-motion-controller-firmware"></a><span data-ttu-id="75618-293">モーションコントローラーのファームウェアを更新操作方法ますか?</span><span class="sxs-lookup"><span data-stu-id="75618-293">How do I update motion controller firmware?</span></span>

<span data-ttu-id="75618-294">モーションコントローラーのファームウェアはヘッドセットドライバーの一部であり、必要に応じて、接続時に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="75618-294">Motion controller firmware is part of the headset driver and will be updated automatically on connection, if necessary.</span></span> <span data-ttu-id="75618-295">通常、ファームウェアの更新は、Bluetooth ラジオとリンクの品質に応じて1-2 分かかります。</span><span class="sxs-lookup"><span data-stu-id="75618-295">Firmware updates typically take 1-2 minutes depending on Bluetooth radio and link quality.</span></span> <span data-ttu-id="75618-296">まれに、コントローラーのファームウェアの更新に最大で10分かかる場合があります。これは、Bluetooth 接続や無線の干渉が低いことを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75618-296">In rare cases, controller firmware updates may take up to 10 minutes, which can indicate poor Bluetooth connectivity or radio interference.</span></span> <span data-ttu-id="75618-297">接続の問題をトラブルシューティングする方法について [は、「Bluetooth のベストプラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75618-297">See [Bluetooth best practices in the Enthusiast Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) to troubleshoot connectivity issues.</span></span> <span data-ttu-id="75618-298">ファームウェアの更新後、コントローラーは再起動し、ホスト PC に再接続します (Led が監視に対して明るくなることがあります)。</span><span class="sxs-lookup"><span data-stu-id="75618-298">After a firmware update, controllers will reboot and reconnect to the host PC (you may notice the LEDs go bright for tracking).</span></span> <span data-ttu-id="75618-299">ファームウェアの更新が中断された場合 (たとえば、コントローラーの電源が切れている場合)、次にコントローラーの電源がオンになったときにもう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="75618-299">If a firmware update is interrupted (for example, the controllers lose power), it will be attempted again the next time the controllers are powered on.</span></span>

### <a name="how-i-can-check-battery-level"></a><span data-ttu-id="75618-300">バッテリレベルを確認するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="75618-300">How I can check battery level?</span></span>

<span data-ttu-id="75618-301">[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)では、コントローラーの電源を入れて、仮想モデルの反対側のバッテリレベルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="75618-301">In the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md), you can turn your controller over to see its battery level on the reverse side of the virtual model.</span></span> <span data-ttu-id="75618-302">物理的なバッテリレベルインジケーターはありません。</span><span class="sxs-lookup"><span data-stu-id="75618-302">There's no physical battery level indicator.</span></span>

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a><span data-ttu-id="75618-303">ヘッドセットなしでこれらのコントローラーを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="75618-303">Can you use these controllers without a headset?</span></span> <span data-ttu-id="75618-304">ジョイスティック/トリガー/その他の入力に対してのみ</span><span class="sxs-lookup"><span data-stu-id="75618-304">Just for the joystick/trigger/etc input?</span></span>

<span data-ttu-id="75618-305">ユニバーサル Windows アプリケーションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="75618-305">Not for Universal Windows Applications.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="75618-306">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="75618-306">Troubleshooting</span></span>

<span data-ttu-id="75618-307">ファンガイドの「 [モーションコントローラーのトラブルシューティング](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75618-307">See [motion controller troubleshooting](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) in the Enthusiast Guide.</span></span>

## <a name="filing-motion-controller-feedbackbugs"></a><span data-ttu-id="75618-308">モーションコントローラーのフィードバック/バグのファイリング</span><span class="sxs-lookup"><span data-stu-id="75618-308">Filing motion controller feedback/bugs</span></span>

<span data-ttu-id="75618-309">"Mixed Reality-> 入力" カテゴリを使用してフィードバックハブに[フィードバックをお](../give-us-feedback.md)寄せください。</span><span class="sxs-lookup"><span data-stu-id="75618-309">[Give us feedback](../give-us-feedback.md) in Feedback Hub, using the "Mixed Reality -> Input" category.</span></span>

## <a name="see-also"></a><span data-ttu-id="75618-310">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="75618-310">See also</span></span>

* [<span data-ttu-id="75618-311">Unity のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="75618-311">Motion controllers in Unity</span></span>](../develop/unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="75618-312">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="75618-312">Hands and motion controllers in DirectX</span></span>](../develop/native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="75618-313">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="75618-313">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="75618-314">愛好家ガイド: Windows Mixed Reality ホーム</span><span class="sxs-lookup"><span data-stu-id="75618-314">Enthusiast's Guide: Your Windows Mixed Reality home</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [<span data-ttu-id="75618-315">愛好家ガイド: Windows Mixed Reality でのゲーム & アプリの使用</span><span class="sxs-lookup"><span data-stu-id="75618-315">Enthusiast's Guide: Using games & apps in Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [<span data-ttu-id="75618-316">インサイドアウト追跡のしくみ</span><span class="sxs-lookup"><span data-stu-id="75618-316">How inside-out tracking works</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
