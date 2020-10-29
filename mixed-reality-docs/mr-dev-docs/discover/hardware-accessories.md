---
title: ハードウェア アクセサリ
description: Windows Mixed Reality で使用できるアクセサリの種類と、それらを設定する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 操作方法、アクセサリ、bluetooth、bt、コントローラー、ゲームパッド、clicker、xbox
ms.openlocfilehash: 7f51264a3914d028c9a027d70d5aa1999582110a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690338"
---
# <a name="hardware-accessories"></a><span data-ttu-id="db58c-104">ハードウェア アクセサリ</span><span class="sxs-lookup"><span data-stu-id="db58c-104">Hardware accessories</span></span>

<span data-ttu-id="db58c-105">Windows Mixed Reality デバイスでは、アクセサリがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="db58c-105">Windows Mixed Reality devices support accessories.</span></span> <span data-ttu-id="db58c-106">Bluetooth または USB を使用して、サポートされているアクセサリを、接続されている PC を使用して、イマーシブヘッドセットにペアリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="db58c-106">You can use Bluetooth or USB to pair supported accessories to an immersive headset by using the PC to which it is connected.</span></span>

<span data-ttu-id="db58c-107">HoloLens での Bluetooth アクセサリの使用の詳細については、「 [bluetooth および USB C デバイスへの接続](https://docs.microsoft.com/hololens/hololens-connect-devices)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db58c-107">For information about using Bluetooth accessories with HoloLens, see [Connect to Bluetooth and USB-C devices](https://docs.microsoft.com/hololens/hololens-connect-devices).</span></span>

<span data-ttu-id="db58c-108">Windows Mixed Reality イマーシブヘッドセットには、 [宝石](../design/gaze-and-commit.md) と [声](../design/voice-input.md)を超えた入力のためのアクセサリが必要です。</span><span class="sxs-lookup"><span data-stu-id="db58c-108">Windows Mixed Reality immersive headsets require accessories for input beyond [gaze](../design/gaze-and-commit.md) and [voice](../design/voice-input.md).</span></span> <span data-ttu-id="db58c-109">サポートされているアクセサリには、 **キーボード、マウス** 、 **ゲームパッド** 、および **[モーションコントローラー](../design/motion-controllers.md)** があります。</span><span class="sxs-lookup"><span data-stu-id="db58c-109">Supported accessories include **keyboard and mouse** , **gamepad** , and **[motion controllers](../design/motion-controllers.md)** .</span></span>

## <a name="pairing-bluetooth-accessories"></a><span data-ttu-id="db58c-110">Bluetooth アクセサリのペアリング</span><span class="sxs-lookup"><span data-stu-id="db58c-110">Pairing Bluetooth accessories</span></span>

<span data-ttu-id="db58c-111">Bluetooth 周辺機器とイマーシブヘッドセットのペアリングは、Bluetooth 周辺機器と Windows 10 デスクトップまたはモバイルデバイスとのペアリングに似ています。</span><span class="sxs-lookup"><span data-stu-id="db58c-111">Pairing a Bluetooth peripheral with an immersive headset is similar to pairing a Bluetooth peripheral with a Windows 10 desktop or mobile device:</span></span>

1. <span data-ttu-id="db58c-112">[スタート] メニューから、[ **設定** ] アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="db58c-112">From the Start Menu, open the **Settings** app</span></span>
2. <span data-ttu-id="db58c-113">**デバイス** にアクセス</span><span class="sxs-lookup"><span data-stu-id="db58c-113">Go to **Devices**</span></span>
3. <span data-ttu-id="db58c-114">Bluetooth ラジオがスライダースイッチを使用してオフになっている場合はオンにする</span><span class="sxs-lookup"><span data-stu-id="db58c-114">Turn on the Bluetooth radio if it is off using the slider switch</span></span>
4. <span data-ttu-id="db58c-115">Bluetooth デバイスをペアリングモードにします。</span><span class="sxs-lookup"><span data-stu-id="db58c-115">Place your Bluetooth device in pairing mode.</span></span> <span data-ttu-id="db58c-116">これは、デバイスによって異なります。</span><span class="sxs-lookup"><span data-stu-id="db58c-116">This varies from device to device.</span></span> <span data-ttu-id="db58c-117">ほとんどの Bluetooth デバイスでは、1つまたは複数のボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="db58c-117">On most Bluetooth devices this is done by pressing and holding one or more buttons.</span></span>
5. <span data-ttu-id="db58c-118">デバイスの名前が Bluetooth デバイスの一覧に表示されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="db58c-118">Wait for the name of the device to show up in the list of Bluetooth devices.</span></span> <span data-ttu-id="db58c-119">その場合は、デバイスを選択し、[ **ペアリング** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="db58c-119">When it does, select the device then select the **Pair** button.</span></span> <span data-ttu-id="db58c-120">近くの Bluetooth デバイスが多数ある場合は、[Bluetooth デバイス] 一覧の一番下までスクロールして、ペアリングしようとしているデバイスを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db58c-120">If you have many Bluetooth devices nearby you may need to scroll to the bottom of the Bluetooth device list to see the device you are trying to pair.</span></span>
6. <span data-ttu-id="db58c-121">Bluetooth 周辺機器と入力機能 (Bluetooth キーボードなど) をペアリングすると、6桁または8桁の pin が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="db58c-121">When pairing Bluetooth peripherals with input capability (e.g.: Bluetooth keyboards), a 6-digit or an 8-digit pin may be displayed.</span></span> <span data-ttu-id="db58c-122">必ず周辺機器に pin を入力し、enter キーを押してヘッドセットのペアリングを完了してください。</span><span class="sxs-lookup"><span data-stu-id="db58c-122">Be sure to type that pin on the peripheral and then press enter to complete pairing with the headset.</span></span>

## <a name="motion-controllers"></a><span data-ttu-id="db58c-123">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="db58c-123">Motion controllers</span></span>

<span data-ttu-id="db58c-124">Windows Mixed Reality [モーションコントローラー](../design/motion-controllers.md) は、HoloLens ではなく、イマーシブヘッドセットでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="db58c-124">Windows Mixed Reality [motion controllers](../design/motion-controllers.md) are supported by immersive headsets, but not HoloLens.</span></span> <span data-ttu-id="db58c-125">これらのコントローラーは、イマーシブヘッドセットのセンサーを使用して、ビューのフィールドの移動を正確かつ迅速に追跡できます。つまり、領域内の壁にハードウェアを取り付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="db58c-125">These controllers offer precise and responsive tracking of movement in your field of view using the sensors in the immersive headset, meaning there is no need to install hardware on the walls in your space.</span></span> <span data-ttu-id="db58c-126">各コントローラーは、いくつかの入力方法を特徴としています。</span><span class="sxs-lookup"><span data-stu-id="db58c-126">Each controller features several methods of input.</span></span>

![Windows Mixed Reality モーションコントローラー](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a><span data-ttu-id="db58c-128">Bluetooth キーボード</span><span class="sxs-lookup"><span data-stu-id="db58c-128">Bluetooth keyboards</span></span>

<span data-ttu-id="db58c-129">English 言語 Qwerty Bluetooth キーボードは、holographic キーボードを使用できる任意の場所でペアにして使用できます。</span><span class="sxs-lookup"><span data-stu-id="db58c-129">English language Qwerty Bluetooth keyboards can be paired and used anywhere you can use the holographic keyboard.</span></span> <span data-ttu-id="db58c-130">品質の高いキーボードを使用すると、違いがあるため、 [Microsoft Universal たたみ込みキーボード](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) または [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="db58c-130">Getting a quality keyboard makes a difference, so we recommend the [Microsoft Universal Foldable Keyboard](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) or the [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).</span></span>

## <a name="bluetooth-gamepads"></a><span data-ttu-id="db58c-131">Bluetooth ゲームパッド</span><span class="sxs-lookup"><span data-stu-id="db58c-131">Bluetooth gamepads</span></span>

<span data-ttu-id="db58c-132">ゲームパッドサポートを特に有効にしたアプリやゲームでコントローラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="db58c-132">You can use a controller with apps and games that specifically enable gamepad support.</span></span> <span data-ttu-id="db58c-133">ゲームパッドは、HoloLens ユーザーインターフェイスを制御するためには使用できません。</span><span class="sxs-lookup"><span data-stu-id="db58c-133">Gamepads cannot be used to control the HoloLens user interface.</span></span>

<span data-ttu-id="db58c-134">Xbox が搭載されている xbox ワイヤレスコントローラー、または xbox One のアクセサリとして販売されている xbox ワイヤレスコントローラーは、HoloLens とイマーシブヘッドセットで使用できるようにする Bluetooth 接続機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="db58c-134">Xbox Wireless Controllers that come with the Xbox One S or sold as accessories for the Xbox One S feature Bluetooth connectivity that enable them to be used with HoloLens and immersive headsets.</span></span> <span data-ttu-id="db58c-135">Xbox ワイヤレスコントローラーを HoloLens で使用するには、その前に [更新する必要があり](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) ます。</span><span class="sxs-lookup"><span data-stu-id="db58c-135">The Xbox Wireless Controller [must be updated](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before it can be used with HoloLens.</span></span>

<span data-ttu-id="db58c-136">Bluetooth ゲームパッドの他のブランドは、Windows Mixed Reality デバイスで動作することがありますが、サポートはアプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="db58c-136">Other brands of Bluetooth gamepads may work with Windows Mixed Reality devices, but support will vary by application.</span></span>

## <a name="other-bluetooth-accessories"></a><span data-ttu-id="db58c-137">その他の Bluetooth アクセサリ</span><span class="sxs-lookup"><span data-stu-id="db58c-137">Other Bluetooth accessories</span></span>

<span data-ttu-id="db58c-138">周辺機器が Bluetooth HID または GATT のいずれかのプロファイルをサポートしている限り、HoloLens とペアリングできます。</span><span class="sxs-lookup"><span data-stu-id="db58c-138">As long as the peripheral supports either the Bluetooth HID or GATT profiles, it will be able to pair with HoloLens.</span></span> <span data-ttu-id="db58c-139">キーボード、マウス、および HoloLens Clicker 以外の他の Bluetooth HID および GATT デバイスでは、完全に機能するためには、Microsoft HoloLens のコンパニオンアプリケーションが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="db58c-139">Other Bluetooth HID and GATT devices besides keyboard, mice, and the HoloLens Clicker may require a companion application on Microsoft HoloLens to be fully functional.</span></span>

<span data-ttu-id="db58c-140">サポートされない周辺機器は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="db58c-140">Unsupported peripherals include:</span></span>

* <span data-ttu-id="db58c-141">Bluetooth オーディオプロファイルの周辺機器はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db58c-141">Peripherals in the Bluetooth audio profiles are not supported.</span></span>
* <span data-ttu-id="db58c-142">Bluetooth オーディオデバイス (スピーカーやヘッドセットなど) は、設定アプリで使用できるように見える場合がありますが、オーディオエンドポイントとして Microsoft HoloLens で使用することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="db58c-142">Bluetooth audio devices such as speakers and headsets may appear as available in the Settings app, but are not supported to be used with Microsoft HoloLens as an audio endpoint.</span></span>
* <span data-ttu-id="db58c-143">Bluetooth 対応の携帯電話および Pc は、ファイル転送にペアリングして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="db58c-143">Bluetooth-enabled phones and PCs are not supported to be paired and used for file transfer.</span></span>

## <a name="unpairing-a-bluetooth-peripheral"></a><span data-ttu-id="db58c-144">Bluetooth 周辺機器のペアリングを解除する</span><span class="sxs-lookup"><span data-stu-id="db58c-144">Unpairing a Bluetooth peripheral</span></span>

1. <span data-ttu-id="db58c-145">[スタート] メニューから、[ **設定** ] アプリを開きます。</span><span class="sxs-lookup"><span data-stu-id="db58c-145">From the Start Menu, open the **Settings** app</span></span>
2. <span data-ttu-id="db58c-146">**デバイス** にアクセス</span><span class="sxs-lookup"><span data-stu-id="db58c-146">Go to **Devices**</span></span>
3. <span data-ttu-id="db58c-147">Bluetooth ラジオがオフになっている場合はオンにする</span><span class="sxs-lookup"><span data-stu-id="db58c-147">Turn on the Bluetooth radio if it is off</span></span>
4. <span data-ttu-id="db58c-148">利用可能な Bluetooth デバイスの一覧でデバイスを検索する</span><span class="sxs-lookup"><span data-stu-id="db58c-148">Find your device in the list of available Bluetooth devices</span></span>
5. <span data-ttu-id="db58c-149">一覧からデバイスを選択し、[ **削除** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="db58c-149">Select your device from the list and then select the **Remove** button</span></span>
