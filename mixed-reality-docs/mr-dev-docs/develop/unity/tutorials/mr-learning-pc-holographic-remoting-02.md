---
title: Holographic Remoting PC アプリケーションを作成する
description: このコースを完了すると、PC アプリケーションを作成して Mixed Reality エクスペリエンスを PC から HoloLens 2 にリモート処理する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, PC Holographic Remoting, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590304"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2.Holographic Remoting PC アプリケーションの作成

このチュートリアルでは、Holographic Remoting 用の PC アプリを作成して、いつでも HoloLens 2 に接続できるようにし、Mixed Reality で 3D コンテンツを視覚化する方法について説明します。

## <a name="objectives"></a>目標

* Holographic Remoting 用に Unity を構成する
* Visual Studio でアプリケーションをビルドして展開する方法を学習する
* Holographic Remoting アプリケーションを開発し、HoloLens に接続する

## <a name="configuring-your-scene-for-holographic-remoting"></a>Holographic Remoting 用のシーンの構成

このセクションでは、Wi-Fi 接続を使用して、PC から HoloLens 2 デバイスに Mixed Reality エクスペリエンスをリアルタイムにストリーミングできるようにプロジェクトを構成します。

[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.PCHolograhicRemoting]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動します。次に、**HolographicRemoting** プレハブをクリックしてシーンにドラッグします。

![新しく追加された HolographicRemoting プレハブがまだ選択されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>アプリケーションを PC にビルドする

これで、Holographic Remoting アプリを PC でビルドする準備ができました。 次の手順に従って変更を行い、PC にこのアプリケーションをビルドします。

### <a name="1-set-the-player-settings"></a>1.プレーヤー設定を設定する

Unity メニューで、[編集] > [プロジェクトの設定] の順に選択して、[プレーヤーの設定] ウィンドウを開きます。

[プロジェクトの設定] ウィンドウで、 **[Publishing Settings]\(発行の設定\)** を展開し、 **[機能]** セクションまで下にスクロールして、既存の機能に加えて以下の機能チェックボックスをオンにします。

* インターネット クライアント サーバー
* プライベート ネットワーク クライアント サーバー

**[XR Settings]\(XR 設定\)** セクションで、 **[WSA Holographic Remoting Supported]\(WSA Holographic Remoting のサポート\)** チェックボックスをオンにして、Holographic Remoting を有効にします。

![[WSA Holographic Remoting Supported]\(WSA Holographic Remoting のサポート\) が有効にされている [XR Settings]\(XR 設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2.Unity プロジェクトをビルドする

Unity メニューで、[ファイル] > [ビルド設定] の順に選択して、[ビルド設定] ウィンドウを開きます。

[Build Settings]\(ビルド設定\) ウィンドウで、***[Add Open Scenes]\(開いているシーンの追加\)** ボタンをクリックして、現在のシーンを [シーン] に追加します。 ビルドの一覧で、_ *_[ビルド] ボタン_** をクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。

![シーンが追加されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納するのに適切な場所 (Documents\MixedRealityLearning など) を選択します。 新しいフォルダーを作成し、PCHolographicRemoting などの適切な名前を付けます。 次に、***[フォルダーの選択]*** ボタンをクリックして、ビルド処理を開始します。

![[フォルダーの選択] プロンプト ウィンドウが表示されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Unity でビルド処理が完了するまで待ちます。

![ビルド処理が進行中の Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3.アプリのビルドと配置

ビルド処理が完了すると、Unity は、ビルドを格納した場所を開くように Windows ファイル エクスプローラーを表示します。 フォルダー内を移動し、.sln ファイルをダブルクリックして Visual Studio で開きます。

![新しく作成された Visual Studio ソリューションが選択された Windows エクスプローラー](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、ツールのインストールに関するドキュメントで示されている、前提条件となるすべてのコンポーネントがインストールされていることをご確認ください。

[リリース] 構成、[x64] アーキテクチャ、ターゲットとして [ローカル コンピューター] を選択して、PC 用に Visual Studio を構成します。

![ローカル コンピューター用に構成された Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

***[ローカル コンピューター]*** と表示されているボタンをクリックします。 PC 上でアプリケーションのビルドとデプロイが開始されます。 既定では、アプリケーションはお使いの PC にインストールされます。

## <a name="testing-holographic-remoting-remote-application"></a>Holographic Remoting リモート アプリケーションのテスト

PC アプリケーションを HoloLens 2 に接続するには、次の手順を実行します。

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1.Remoting Player アプリケーションを HoloLens 2 デバイスにインストールする

* HoloLens 2 で、Store アプリにアクセスし、"**Remoting Player**" を検索します。
* **Remoting Player** アプリを選択します。
* **[インストール]** をタップし、アプリをダウンロードしてインストールします。

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2.Holographic Remoting PC アプリを Remoting Player に接続する

* HoloLens で **Remoting Player** を起動します。
* HoloLens の **IP アドレス** をメモしておきます。 これは、**Remoting Player** が起動した直後に Remoting Player によってホログラムとして表示されます。
* Holographic Remoting PC アプリケーションを PC で開きます。
* アプリケーションが起動したら、**IP アドレス** を入力し、 **[接続]** ボタンをクリックして接続します。

## <a name="congratulations"></a>結論

このチュートリアルでは、Holographic Remoting リモート アプリを作成していつでも HoloLens 2 に接続できるようにし、Mixed Reality で 3D コンテンツを視覚化する方法について学習しました。 HoloLens が Holographic Remoting PC アプリケーションに接続されると、Mixed Reality エクスペリエンスが HoloLens 2 デバイスにストリーミングされているのを確認できます。
