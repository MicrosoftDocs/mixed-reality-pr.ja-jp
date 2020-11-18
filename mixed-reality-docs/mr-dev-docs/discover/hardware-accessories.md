---
title: ハードウェア アクセサリ
description: Windows Mixed Reality で使用できるアクセサリの種類と、それらを設定する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 操作方法、アクセサリ、bluetooth、bt、コントローラー、ゲームパッド、clicker、xbox、ハードウェア、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、モーションコントローラー
ms.openlocfilehash: 3855d5337c4cad462b60ff8c73cec0b7b96c0ca1
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702008"
---
# <a name="hardware-accessories"></a>ハードウェア アクセサリ

Windows Mixed Reality デバイスでは、アクセサリがサポートしています。 Bluetooth または USB を使用して、サポートされているアクセサリを、接続されている PC を使用して、イマーシブヘッドセットにペアリングすることができます。

HoloLens での Bluetooth アクセサリの使用の詳細については、「 [bluetooth および USB C デバイスへの接続](https://docs.microsoft.com/hololens/hololens-connect-devices)」を参照してください。

Windows Mixed Reality イマーシブヘッドセットには、 [宝石](../design/gaze-and-commit.md) と [声](../design/voice-input.md)を超えた入力のためのアクセサリが必要です。 サポートされているアクセサリには、 **キーボード、マウス**、 **ゲームパッド**、および **[モーションコントローラー](../design/motion-controllers.md)** があります。

## <a name="pairing-bluetooth-accessories"></a>Bluetooth アクセサリのペアリング

Bluetooth 周辺機器とイマーシブヘッドセットのペアリングは、Bluetooth 周辺機器と Windows 10 デスクトップまたはモバイルデバイスとのペアリングに似ています。

1. [スタート] メニューから、[ **設定** ] アプリを開きます。
2. **デバイス** にアクセス
3. Bluetooth ラジオがスライダースイッチを使用してオフになっている場合はオンにする
4. Bluetooth デバイスをペアリングモードにします。 これは、デバイスによって異なります。 ほとんどの Bluetooth デバイスでは、1つまたは複数のボタンを押したままにします。
5. デバイスの名前が Bluetooth デバイスの一覧に表示されるまで待ちます。 その場合は、デバイスを選択し、[ **ペアリング** ] ボタンを選択します。 近くの Bluetooth デバイスが多数ある場合は、[Bluetooth デバイス] 一覧の一番下までスクロールして、ペアリングしようとしているデバイスを確認する必要があります。
6. Bluetooth 周辺機器と入力機能 (Bluetooth キーボードなど) をペアリングすると、6桁または8桁の pin が表示される場合があります。 必ず周辺機器に pin を入力し、enter キーを押してヘッドセットのペアリングを完了してください。

## <a name="motion-controllers"></a>モーション コントローラー

Windows Mixed Reality [モーションコントローラー](../design/motion-controllers.md) は、HoloLens ではなく、イマーシブヘッドセットでサポートされています。 これらのコントローラーは、イマーシブヘッドセットのセンサーを使用して、ビューのフィールドの移動を正確かつ迅速に追跡できます。つまり、領域内の壁にハードウェアを取り付ける必要はありません。 各コントローラーは、いくつかの入力方法を特徴としています。

![Windows Mixed Reality モーションコントローラー](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth キーボード

English 言語 Qwerty Bluetooth キーボードは、holographic キーボードを使用できる任意の場所でペアにして使用できます。 品質の高いキーボードを使用すると、違いがあるため、 [Microsoft Universal たたみ込みキーボード](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) または [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)をお勧めします。

## <a name="bluetooth-gamepads"></a>Bluetooth ゲームパッド

ゲームパッドサポートを特に有効にしたアプリやゲームでコントローラーを使用できます。 ゲームパッドは、HoloLens ユーザーインターフェイスを制御するためには使用できません。

Xbox が搭載されている xbox ワイヤレスコントローラー、または xbox One のアクセサリとして販売されている xbox ワイヤレスコントローラーは、HoloLens とイマーシブヘッドセットで使用できるようにする Bluetooth 接続機能を備えています。 Xbox ワイヤレスコントローラーを HoloLens で使用するには、その前に [更新する必要があり](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) ます。

Bluetooth ゲームパッドの他のブランドは、Windows Mixed Reality デバイスで動作することがありますが、サポートはアプリケーションによって異なります。

## <a name="other-bluetooth-accessories"></a>その他の Bluetooth アクセサリ

周辺機器が Bluetooth HID または GATT のいずれかのプロファイルをサポートしている限り、HoloLens とペアリングできます。 キーボード、マウス、および HoloLens Clicker 以外の他の Bluetooth HID および GATT デバイスでは、完全に機能するためには、Microsoft HoloLens のコンパニオンアプリケーションが必要になる場合があります。

サポートされない周辺機器は次のとおりです。

* Bluetooth オーディオプロファイルの周辺機器はサポートされていません。
* Bluetooth オーディオデバイス (スピーカーやヘッドセットなど) は、設定アプリで使用できるように見える場合がありますが、オーディオエンドポイントとして Microsoft HoloLens で使用することはサポートされていません。
* Bluetooth 対応の携帯電話および Pc は、ファイル転送にペアリングして使用することはできません。

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 周辺機器のペアリングを解除する

1. [スタート] メニューから、[ **設定** ] アプリを開きます。
2. **デバイス** にアクセス
3. Bluetooth ラジオがオフになっている場合はオンにする
4. 利用可能な Bluetooth デバイスの一覧でデバイスを検索する
5. 一覧からデバイスを選択し、[ **削除** ] ボタンを選択します。
