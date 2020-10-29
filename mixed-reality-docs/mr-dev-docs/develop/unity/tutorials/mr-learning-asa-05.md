---
title: Azure Spatial Anchors チュートリアル - 5. Android と iOS 用の Azure Spatial Anchors
description: このコースを完了すると、Mixed Reality ツールキットと Azure Spatial Anchors を使用して Android および iOS に Unity プロジェクトをデプロイする方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, Android, iOS
ms.localizationpriority: high
ms.openlocfilehash: f1c1ab7c9a79108931762b31640ff667fe1fc2e5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700235"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5.Android と iOS 用の Azure Spatial Anchors

このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について説明します。

## <a name="objectives"></a>目標

* Unity の AR Foundation と ARCore XR Plugin を使用して、ご利用の Android デバイス用にプロジェクトをビルドする方法について学習します。
* Unity の AR Foundation と ARKit XR Plugin を使用して、ご利用の iOS デバイス用にプロジェクトをビルドする方法について学習します。

## <a name="installing-inbuilt-unity-packages"></a>組み込みの Unity パッケージのインストール

このセクションでは、次の組み込みパッケージをアップグレードしてインストールします。

* AR Foundation 3.1.3
* XR Legacy Input Helpers 2.1.4
* ARCore XR Plugin 3.1.3 for Android のサポート
* ARKit XR Plugin 3.1.3 for iOS のサポート

> [!CAUTION]
> すべてのバージョンが MRTK と互換性があるわけではなく、特定のバージョンのみが連携して機能するため、必ず上記のバージョンをインストールしてください。

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]**  >  **[3.1.3]** の順に選択し、 **[3.1.3 に更新します]** ボタンをクリックしてパッケージを更新します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

必要に応じて、同じプロセスに従って残りのパッケージをインポートします。

> [!NOTE]
> Android 用にこのプロジェクトを開発している場合は、ARKit XR Plugin パッケージをインストールする必要はありません。 同様に、iOS 用にこのプロジェクトを開発している場合は、ARCore XR Plugin をインストールする必要はありません。

## <a name="configure-mrtk-for-ar-foundation-camera"></a>AR Foundation Camera 用に MRTK を構成する

このセクションでは、モバイル デバイスに展開するために MRTK を構成する方法について学習します。

[Hierarchy]\(階層\) ウィンドウで、 **[MixedRealityToolkit]** オブジェクトを選択します。 次に、[Inspector]\(インスペクター\) ウィンドウで、 **[Camera]\(カメラ\)** タブを選択し、カメラ プロファイルを複製して、それに適切な名前 (たとえば **AzureSpatialAnchors_ARCameraProfile** ) を付けます。

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> MRTK プロファイルを複製する方法については、[Mixed Reality ツールキット プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。

[Inspector]\(インスペクター\) ウィンドウで **[Camera]\(カメラ\)** タブを選択したままにして、 **[Camera Setting Providers]\(カメラ設定プロバイダー\)** を展開し、 **[+ Add Camera Setting Provider]\(+ カメラ設定プロバイダーの追加\)** ボタンをクリックします。次に、新しく追加した **[New data provider 1]\(新しいデータ プロバイダー 1\)** を展開します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

**[Type]\(種類\)** ドロップダウンを使用して、種類を **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** に変更します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択したままにして、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、次のコンポーネントを追加します。

* AR Anchor Manager (スクリプト)
* DisableDiagnosticsSystem (スクリプト)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> AR Reference Point Manager (スクリプト) コンポーネントを追加すると、AR Session Origin (スクリプト) コンポーネントも自動的に追加されます。AR Reference Point Manager (スクリプト) コンポーネントで必要になるためです。

## <a name="building-your-application-to-your-android-device"></a>ご利用の Android デバイス用のアプリケーションのビルド

このセクションでは、プロジェクトを Android デバイス用にビルドして配置するように構成する方法について学習します。

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択し、[Build Settings]\(ビルド設定\) ウィンドウを開いて、プラットフォームを Android に変更します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> ビルド プラットフォームを切り替える方法については、「[ビルド プラットフォームの切り替え](mr-learning-base-02.md#switching-the-build-platform)」にある手順を参照してください。

[ビルド設定] ウィンドウを閉じます。

Unity メニューで、 **[Mixed Reality ツールキット]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウを開きます。すべてのオプションを確実に選択してから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクトの設定...\)** の順に選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[他の設定]** セクションを見つけます。 **[Vulkan]** を選択してから、 **"-"** シンボルをクリックしてそれを削除します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

[Player Settings]\(プレーヤーの設定\) ウィンドウを閉じ、もう一度 [ビルド設定] ウィンドウを開きます。

[ビルドの設定] ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、 **[Scenes in Build]\(ビルド内のシーン\)** リストに現在のシーンを追加します。 次に、USB ケーブルを使用して、使用する Android デバイスを自分のコンピューターに接続し、 **[Run Device]\(デバイスの実行\)** ドロップダウンからそれを選択します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> そのデバイスが [Run Device]\(デバイスの実行\) ドロップダウンに表示されない場合は、ドロップダウンの横にある [更新] ボタンを押してみてください。

[ビルド設定] ウィンドウで、 **[ビルドして実行]** ボタンをクリックして、[Android のビルド] ウィンドウを開きます。

ビルドを格納するのに適切な場所 (たとえば _D:\MixedRealityLearning\Builds_ ) を選択してから、apk に適切な名前 ( _たとえば、MRTKTutorials-AzureSpatialAnchors_ ) を指定し、 **[保存]** ボタンをクリックしてビルド プロセスを開始します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Unity コンソール ウィンドウに、Android SDK、NDK、または JDK モジュールに関連するエラーが表示される場合は、Unity ハブを開き、その関連する Android ビルド サポート モジュールをインストールする必要があります。

ビルド プロセスが完了すると、アプリがご利用の Android デバイスに自動的に読み込まれます。

## <a name="building-your-application-to-your-ios-device"></a>ご利用の iOS デバイス用のアプリケーションのビルド

このセクションでは、プロジェクトを iOS デバイス用にビルドして配置するように構成する方法について学習します。

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択し、[Build Settings]\(ビルド設定\) ウィンドウを開き、プラットフォームを iOS に変更します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> ビルド プラットフォームを切り替える方法については、「[ビルド プラットフォームの切り替え](mr-learning-base-02.md#switching-the-build-platform)」にある手順を参照してください。

[ビルド設定] ウィンドウを閉じます。

Unity メニューで、 **[Mixed Reality ツールキット]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウを開きます。すべてのオプションを確実に選択してから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクトの設定...\)** の順に選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[他の設定]** セクションを見つけます。 **[Strip Engine Code]\(ストリップ エンジン コード\)** チェックボックスをオフにして、それを無効にします。

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

[Player Settings]\(プレーヤーの設定\) ウィンドウを閉じ、もう一度 **[ビルド設定]** ウィンドウを開きます。

[ビルドの設定] ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、 **[Scenes in Build]\(ビルド内のシーン\)** リストに現在のシーンを追加します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

[ビルド設定] ウィンドウで、 **[ビルド]** ボタンをクリックして、[iOS のビルド] ウィンドウを開きます。

Xcode プロジェクトを格納するのに適切な場所 (たとえば _D:\MixedRealityLearning\Builds_ ) を選択し、新しいフォルダーを作成してそれに適切な名前 (たとえば _MRTKTutorials-AzureSpatialAnchors_ ) を指定してから、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

ビルド プロセスが完了したら、「[Xcode プロジェクトをエクスポートする](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)」にある手順に従って、Xcode プロジェクトを iOS デバイスにデプロイする方法を学習します。

## <a name="congratulations"></a>結論

このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について学習しました。
