---
title: HoloLens 2 用 PIX のインストール
description: HoloLens 2 デバイス用の PIX をインストールする方法について説明します。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens、HoloLens 2、PIX、capture、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615362"
---
# <a name="installing-pix-for-hololens-2"></a>HoloLens 2 用 PIX のインストール

[PIX](https://devblogs.microsoft.com/pix) は、Windows 上の DirectX 12 アプリケーション用のパフォーマンスチューニングおよびデバッグツールです。 

## <a name="setup"></a>セットアップ

1. ホスト PC から最新の PIX [リリース]( https://devblogs.microsoft.com/pix/download) を入手し、USB ケーブル経由で HoloLens 2 を PC に接続します。

2. HoloLens 2 が [Windows Insider ビルド](https://insider.windows.com) にある場合、または PIX を中断する構成がある場合は、  [デバイスを再フラッシュ](https://docs.microsoft.com/hololens/hololens-recovery) してすべてのデータを消去します。

3. **開発者モード** と **デバイスポータル** を有効にする:

* シェルから **設定** を開く:

![[設定] ボタンが強調表示されている HoloLens メニューのスクリーンショット](images/pix-img-01.jpg)

* [ **Update & Security**] を選択します。

![[更新とセキュリティ] ボタンが強調表示されている HoloLens で開かれている [設定] ウィンドウのスクリーンショット](images/pix-img-02.jpg)

* [ **開発者] を** クリックします。

![[開発者用に開く] ボタンが強調表示されている [セキュリティと更新プログラム] ウィンドウのスクリーンショット](images/pix-img-03.jpg)

* **開発者機能を使用** して **デバイスポータルを有効** にする

![[デバイスポータルを有効にする] ボタンが強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-04.jpg)

![[開発機能を使用して設定] で開いている開発者ウィンドウのスクリーンショットの表示/非表示](images/pix-img-05.jpg)

* デバイスが接続された状態で、ユーザーがログインした状態で、Visual Studio を起動します。

> [!IMPORTANT]
> デバイスがスタンバイモードまたはスリープ状態になっていないことを確認します。 この手順で問題が発生した場合は、 [Windows デバイスポータルの手順](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)を参照してください。

## <a name="preparing-for-deployment"></a>展開の準備

1. Visual Studio で、 **ARM64** をデバイスとしてプラットフォームと **デバイス** として設定します。

![プラットフォームとデバイスの設定が強調表示されている visual studio ソリューションのスクリーンショット](images/pix-img-06.png)

2. Visual Studio によって、デバイスからの **PIN** の入力が求められます。

![PIN を要求する visual studio ポップアップのスクリーンショット](images/pix-img-07.png)

* シェルから **設定** を選択する
* **更新プログラム & セキュリティ** を選択する
* [**デバイスの検出**] の下にある [**開発者**] をクリックしてペアを押す 

![デバイス検出が強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-08.jpg)

![登録コードが強調表示されている、有料デバイスのポップアップのスクリーンショット](images/pix-img-09.jpg)

* Visual Studio で生成された PIN 番号を入力します

3. Visual Studio は接続されている HoloLens 2 にアプリをデプロイします。アプリによっては数分かかる場合があります。

## <a name="launching-pix"></a>PIX の起動

まず、デバイスポータルを使用して、HoloLens 2 でアプリが実行されていないことを確認します。 次に、PIX を起動してデバイスに接続し、[ **ホーム**] をクリックします。

![PIX アプリケーションのホーム画面のスクリーンショット](images/pix-img-10.png)

* 左側のメニューから [ **接続** ] を選択します。

![[接続] ボタンが強調表示されている、PIX アプリケーションの左側のメニューのスクリーンショット](images/pix-img-11.png)

2. [ **コンピューター** ] タブで [ **追加** ] をクリックし、次の資格情報を入力します。
    * エイリアス: ユーザーの裁量
    * ホスト名または IP アドレス: 127.0.0.1

3. [**コンピューター** ] タブの右下にある [**接続**] をクリックします。

![[エイリアス]、[ホスト名]、[IP アドレス]、[追加] ボタンが強調表示されている PIX アプリケーション接続ウィンドウのスクリーンショット](images/pix-img-12.png)

> [!NOTE]
> バイナリがコピーされるため、最初の接続は常に低速です。

4. PIX が HoloLens 2 に接続されている場合は、[UWP の起動] タブの [ **ターゲットプロセスの選択** ] セクションでアプリを見つけ、[ **起動**] をクリックします。

![[ターゲットプロセスの選択] ウィンドウと [起動] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-13.png)

## <a name="gpu-captured"></a>キャプチャされた GPU

1. Gpu **キャプチャ** セクションの [**写真**] をクリックして、gpu キャプチャを開始します。

![GPU キャプチャが強調表示された状態で、PC 接続パネルが開いている PIX アプリケーションのスクリーンショット](images/pix-img-14.png)

2. **GPU キャプチャ** パネルで生成されたスクリーンショットをクリックして、分析用のキャプチャを開きます。

![[Gpu キャプチャ] パネルが強調表示されている GPU キャプチャセクションがある PIX アプリケーションのスクリーンショット](images/pix-img-15.png)

3. [ **Start (開始** ) を押して分析を開始します。

![[スタート] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-16.png)

> [!IMPORTANT]
> GPU キャプチャを行った後でタイミングデータを収集する場合は、ヘッドセットを再起動する必要があります。 これはデバイスの1回限りの再起動であり、タイミングデータの収集に必要です。

PIX が使用できるようになりました。

## <a name="see-also"></a>関連項目
* [PIX ホームページ](https://devblogs.microsoft.com/pix)