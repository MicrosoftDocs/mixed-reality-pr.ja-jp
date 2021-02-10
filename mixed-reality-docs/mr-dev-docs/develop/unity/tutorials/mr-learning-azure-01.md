---
title: HoloLens 2 用の Azure Cloud Services
description: このコースを完了すると、HoloLens 2 アプリケーション内でさまざまな Azure サービスを実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Azure, Mixed Reality, Unity, チュートリアル, Hololens, Hololens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchors, Azure Bot Framework, Azure クラウド サービス, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 60ca15ebccaa8348ebd47f7d4bf6245ca1496775
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590704"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1.HoloLens 2 用の Azure Cloud Services

このチュートリアル シリーズへようこそ。ここでは、**Azure クラウド** サービスを **HoloLens 2** アプリケーションに導入することに重点を置いています。 この 5 部構成のチュートリアル シリーズでは、複数の **Azure クラウド** サービスを **HoloLens 2** 用の **Unity** プロジェクトに統合する方法について学習します。 連続する各章では、新しい **Azure クラウド** サービスを追加して、アプリケーションの機能とユーザー エクスペリエンスを拡張しながら、各 **Azure クラウド** サービスの基礎について学びます。

> [!NOTE]
> このチュートリアル シリーズでは **HoloLens 2** に重点を置いていますが、Unity のクロスプラットフォームの性質により、学習内容のほとんどがデスクトップおよび Smartphone アプリケーションにも適用されます。

この最初のチュートリアルでは、シリーズの目標、使用する各 Azure Cloud サービス、および最初の Unity プロジェクトの設定について紹介します。

2 番目のチュートリアルである「[Azure Storage の統合](mr-learning-azure-02.md)」では、Azure Storage をデモ アプリケーションの永続化ソリューションとして統合することから始めます。 また、Blob Storage と Table Storage の違いについて学習し、必要なプロジェクト リソースを準備して、シーンを設定します。 最後に、データの読み取り、更新、および削除操作を確認する方法について説明します。

3 番目のチュートリアルである、「[Azure Custom Vision の統合](mr-learning-azure-03.md)」に進んで、Azure Custom Vision を使用して、HoloLens 2 アプリケーションで画像をトレーニングおよび検出します。 この章では、まず、独自の Azure Custom Vision リソースを設定し、シーン コンポーネントを準備し、アプリケーション内部から独自の画像をトレーニングおよび検出してアクションを開始します。

次に、4 番目のチュートリアルである、「[Azure Spatial Anchors の統合](mr-learning-azure-04.md)」に進んで、Azure Spatial Anchors サービスを調べて場所の保存と検索を行い、主要概念について学習し、必要なリソースを準備し、シーンを設定してアプリケーションでの新機能の使用を開始します。

[Azure Bot Service と LUIS との統合](mr-learning-azure-05.md)に関する、5 番目のチュートリアルでは、アプリケーションに自然言語という新しいユーザー操作の方法を与えることで完了します。 この機能は、Azure Bot Framework を Language Understanding (LUIS) と共に使用することで実現されます。 この最後の章では、Azure Bot Service の基本について説明し、プロセスを高速化するために、Bot Framework Composer をゼロ コード ソリューションとして使用します。 ボットが作成されたら、それをシーンに統合し、HoloLens 2 アプリケーションの最終ステージで実行します。

## <a name="application-goals"></a>アプリケーションの目標

このチュートリアル シリーズでは、画像からオブジェクトを検出し、その空間位置を見つけることができる **HoloLens 2** アプリケーションをビルドします。 ドメインの言語を設定するために、**追跡対象オブジェクト** からこのようなエンティティを呼び出すことができます。
ユーザーは **追跡対象オブジェクト** を作成し、コンピューター ビジョンまたは空間位置、あるいはその両方を使用して画像のセットを関連付けることができます。 すべてのデータをクラウドに保存する必要があります。 さらに、アプリケーションの一部の側面は、ボットを通じてサポートされる自然言語によって制御されることもあります。

### <a name="features"></a>機能

* データと画像の基本的な管理
* 画像のトレーニングと検出
* 空間位置の格納とそのガイダンス
* 自然言語を介して一部の機能を使用するためのボット サポート

## <a name="azure-cloud-services"></a>Azure クラウド サービス

以下の **Azure Cloud** サービスを使用して、上の機能を実装します。

### <a name="azure-storage"></a>Azure Storage に関するページ

永続化ソリューションには、[Azure Storage](https://azure.microsoft.com/services/storage/) を使用します。 これにより、データをテーブルに格納し、画像のような大きなバイナリをアップロードすることができます。

### <a name="azure-custom-vision"></a>Azure Custom Vision

[Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) ([Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) の一部) を使用すると、画像のセットを "*追跡対象オブジェクト*" に関連付けたり、そのセットで機械学習モデルをトレーニングしたり、"*追跡対象オブジェクト*" を検出したりすることができます。

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

"*追跡対象オブジェクト*" の場所を格納し、それを見つけられるようにガイドするには、[Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/) を使用します。

### <a name="azure-bot-service"></a>Azure Bot Service

アプリケーションは主に従来の UI で起動するため、[Azure Bot Service](https://azure.microsoft.com/services/bot-service/) を使用して、何らかの個性を加え、新しい操作方法として機能するようにします。

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[入門チュートリアル](mr-learning-base-01.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity エディターからテストする場合は、接続された Web カメラ
* Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!CAUTION]
> このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。

最初に、「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従います (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*Azure クラウド チュートリアル*" などの適切な名前を付ける
2. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity プロジェクトを構成する](mr-learning-base-02.md#configuring-the-unity-project)
6. [シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureCloudServices* などの適切な名前を付ける

その後、「[空間認識表示オプションを変更する](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルが **DefaultXRSDKConfigurationProfile** であることを確認し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。

## <a name="installing-inbuilt-unity-packages"></a>組み込みの Unity パッケージのインストール

Unity メニューで、 **[ウィンドウ]**  >  **[パッケージ マネージャー]** の順に選択して、[パッケージ マネージャー] ウィンドウを開きます。その後、 **[AR Foundation]** を選択し、 **[インストール]** ボタンをクリックしてパッケージをインストールします。

![AR Foundation が選択されている Unity Package Manager ウィンドウ](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。これは、次のセクションでインポートします。

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

AzurespatialAnchors SDK V2.7.1 を Unity プロジェクトに追加します。パッケージを追加するには、こちらの[チュートリアル](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)に従ってください

次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[チュートリアルのアセットのインポート](mr-learning-base-04.md#importing-the-tutorial-assets)」の手順を参照してください。

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-azure/tutorial1-section4-step1-1.png)

> [!NOTE]
> "WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" と "WorldAnchor.GetNativeSpatialAnchorPtr()" が廃止されていることに関する CS0618 警告が表示されても、無視してかまいません。

## <a name="creating-and-preparing-the-scene"></a>シーンの作成と準備
<!-- TODO: Consider renaming to 'Preparing the scene' -->

このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。

[プロジェクト] ウィンドウで、**Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** フォルダーの順に移動します。 CTRL ボタンを押したまま、 **[SceneController]** 、 **[RootMenu]** および **[DataManager]** をクリックして、3 つのプレハブを選択します。

![SceneController、RootMenu、DataManager の各プレハブが選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (プレハブ)** には、**SceneController (スクリプト)** と **UnityDispatcher (スクリプト)** の 2 つのスクリプトが含まれています。 **SceneController** スクリプト コンポーネントには、いくつかの UX 関数が含まれており、写真キャプチャ機能が促進されますが、**UnityDispatcher** は、Unity メイン スレッドでのアクションの実行を許可するヘルパー クラスです。

**RootMenu (プレハブ)** は、さまざまな小さいスクリプト コンポーネントを介して相互に接続され、アプリケーションの一般的な UX フローを制御する UI ウィンドウをすべて保持する主要な UI プレハブです。

**DataManager (プレハブ)** は、Azure Storage との対話を担当します。これについては、次のチュートリアルで詳しく説明します。

ここで、3 つのプレハブを選択したまま、それらを [階層] ウィンドウにドラッグしてシーンに追加します。

![新しく追加された SceneController、RootMenu、DataManager の各プレハブがまだ選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-2.png)

シーン内のオブジェクトに焦点を合わせるために、**RootMenu** オブジェクトをダブルクリックし、もう一度少しズームアウトすることができます。

![RootMenu オブジェクトが選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。

## <a name="configuring-the-scene"></a>シーンの構成

このセクションでは、*SceneManager*、*DataManager* および *RootMenu* を一緒に接続し、作業シーンを次の「[Azure Storage の統合](mr-learning-azure-01.md)」チュートリアルのために準備します。

### <a name="connect-the-objects"></a>オブジェクトを接続する

[階層] ウィンドウで、**DataManager** オブジェクトを選択します。

![DataManager オブジェクトが選択されている Unity](images/mr-learning-azure/tutorial1-section6-step1-1.png)

[インスペクター] ウィンドウで、**DataManager (Script)** コンポーネントを見つけます。**On Data Manager Ready ()** イベントには空のスロットが表示されます。 ここで、[階層] ウィンドウから、**SceneController** オブジェクトを **On Data Manager Ready ()** イベントにドラッグします。

![DataManager イベント リスナーが追加された Unity](images/mr-learning-azure/tutorial1-section6-step1-2.png)

イベントのドロップダウン メニューがアクティブになったことがわかります。このドロップダウン メニューをクリックして、**SceneController** に移動し、サブ メニューで **[Init ()]** オプションを選択します。

![DataManager イベント アクションが追加された Unity](images/mr-learning-azure/tutorial1-section6-step1-3.png)

[階層] ウィンドウで **SceneController** オブジェクトを選択すると、[インスペクター] に **SceneController** (スクリプト) コンポーネントが表示されます。

![SceneController が選択されている Unity](images/mr-learning-azure/tutorial1-section6-step1-4.png)

設定されていないフィールドがいくつかあることがわかります。これを変更してみましょう。 **DataManager** オブジェクトを [階層] から *[データ マネージャー]* フィールドに移動し、**RootMenu** GameObject を [階層] から *[メイン メニュー]* フィールドに移動します。

![SceneController が構成された Unity](images/mr-learning-azure/tutorial1-section6-step1-5.png)

これで、今後のチュートリアルのためにシーンの準備ができました。 これは必ずプロジェクトに保存してください。

## <a name="prepare-project-build-pipeline"></a>プロジェクト ビルド パイプラインを準備する

プロジェクトにはまだコンテンツが入力されていませんが、いくつかの準備を行い、プロジェクトを **HoloLens 2** 用にビルドできるようにする必要があります。

### <a name="1-add-additional-required-capabilities"></a>1.必要な機能をさらに追加する

Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。

![[Project Settings]\(プロジェクト設定\) が開かれている Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

[Project Settings]\(プロジェクトの設定\) ウィンドウで、 **[Player]\(プレーヤー\)** **[Publishing Settings]\(公開の設定\)** の順に選択します。

![Unity の [Publishing Settings]\(公開の設定\)](images/mr-learning-azure/tutorial1-section7-step1-2.png)

**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールし、チュートリアルの最初にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone** および **SpatialPerception** の機能が有効になっていることを再確認します。 その後、**InternetClientServer**、**PrivateNetworkClientServer**、および **Webcam** の機能を有効にします。

![Unity の機能](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.HoloLens 2 にアプリをデプロイする

このチュートリアル シリーズで使用するすべての機能が、Unity エディター内で実行できるわけではありません。つまり、アプリケーションを HoloLens 2 デバイスにデプロイする方法についてよく理解しておく必要があります。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[入門チュートリアル」のデバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)に関するセクションの手順を参照してください。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.HoloLens 2 でアプリを実行し、アプリ内の指示に従う

> [!CAUTION]
> すべての Azure Services でインターネットが使用されるため、デバイスがインターネットに接続されていることを確認してください。

アプリケーションがデバイスで実行されている場合は、次の要求された機能へのアクセスを受け入れます。

* マイク
* カメラ

これらの機能は、"*チャット ボット*" や *Custom Vision* などのサービスを正しく機能させるために必要です。

## <a name="congratulations"></a>結論

このチュートリアルでは、チュートリアル シリーズの概要を確認し、実装する機能についてと、*HoloLens 2* アプリケーションの実行と **Azure クラウド** サービスがどのように結び付いているかについて学習しました。 必要なコンポーネントをプロジェクトに追加し、このチュートリアル シリーズのためにシーンを準備しました。

次のレッスンでは、データと画像を格納するためのクラウド ベースの永続化ソリューションとして、Azure Storage を使用します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 2.Azure Storage の統合](mr-learning-azure-02.md)
