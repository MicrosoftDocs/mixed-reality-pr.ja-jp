---
title: Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Azure Spatial Anchors を使用して Mixed Reality アプリケーション内でオブジェクトを固定する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: 60d4ae99629f0caf7e5cc7e73b05ed35ee3f4ac4
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699219"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2.Azure Spatial Anchors をお使いになる前に

このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、および単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。

## <a name="objectives"></a>目標

* HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する
* Spatial Anchors を作成し、それらを Azure からフェッチする方法を学習する

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

最初に、「[プロジェクトの初期化と最初のアプリケーションの配置](mr-learning-base-02.md)」に従います (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける
2. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity プロジェクトを構成する](mr-learning-base-02.md#configuring-the-unity-project)
6. [シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureSpatialAnchors* などの適切な名前を付ける

次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の指示に従い、次の作業を行います。

1. **MRTK 構成プロファイル** を **DefaultHoloLens2ConfigurationProfile** に変更します
1. **空間認識メッシュ表示オプション** を **[Occlusion]\(オクルージョン\)** に変更します

## <a name="installing-inbuilt-unity-packages"></a>組み込みの Unity パッケージのインストール

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。

![AR Foundation が選択されている [Package Manager]\(パッケージ マネージャー\) が表示された Unity](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。これは、次のセクションでインポートします。

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

AzurespatialAnchors SDK V2.7.1 を Unity プロジェクトに追加します。パッケージを追加するには、こちらの[チュートリアル](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)に従ってください

次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。


* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> "WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" が廃止されていることに関する CS0618 警告が表示されても、無視してかまいません。

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動し、次のプレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。

* **ButtonParent** プレハブ
* **DebugWindow** プレハブ
* **Instructions** プレハブ
* **ParentAnchor** プレハブ

![新しく追加されたプレハブが選択されている Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合など)、上の画像で示すように、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは、スクリプトをシーンに追加して、アプリでのローカル アンカーと Azure Spatial Anchors の両方の基本的な動作を示す一連のボタン イベントを作成します。

[Hierarchy]\(階層\) ウィンドウで、 **[ButtonParent]** オブジェクトを展開し、**StartAzureSession** という名前の最初の子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![StartAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

[Hierarchy]\(階層\) ウィンドウで、次の **StopAzureSession** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StopAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![StopAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

[Hierarchy]\(階層\) ウィンドウで、次の **CreateAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[CreateAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します
* **[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、CreateAzureAnchor () 関数の引数にします

![CreateAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

[Hierarchy]\(階層\) ウィンドウで、次の **RemoveLocalAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[RemoveLocalAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します
* **[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、RemoveLocalAnchor () 関数の引数にします

![RemoveLocalAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

[Hierarchy]\(階層\) ウィンドウで、次の **FindAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[FindAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![FindAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

[Hierarchy]\(階層\) ウィンドウで、次の **DeleteAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。

* **DeleteAzureAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[DeleteAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![DeleteAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>シーンを Azure リソースに接続する

[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントを見つけます。 このチュートリアル シリーズの「[前提条件](mr-learning-asa-01.md#prerequisites)」の一環として作成した Azure Spatial Anchors アカウントの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。

* **"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの **アカウント ID** を貼り付ける
* **"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける

![Spatial Anchor Manager が構成された Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Azure Spatial Anchors の基本的な動作を試す

Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、ご利用のデバイスにプロジェクトをビルドし、アプリをデプロイする必要があります。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 用のアプリケーションの構築](mr-learning-base-02.md#building-your-application-to-your-hololens-2)の手順に関するページを参照してください。

ご利用のデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。

1. キューブを別の場所に移動します
1. Azure セッションを開始します
1. Azure Anchor を作成します (キューブの場所に Anchor を作成します)。
1. Azure セッションを停止します
1. ローカル アンカーを削除します (これにより、ユーザーはキューブを移動できます)
1. キューブを別の場所に移動します
1. Azure セッションを開始します
1. Azure Anchor を見つけます (手順 3 の場所にキューブを配置します)
1. Azure Anchor を削除します
1. Azure セッションを停止します

![Instructions オブジェクトが選択されている Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors では、インターネットを使用してアンカー データの保存と読み込みを行うため、ご利用のデバイスがインターネットに接続されていることを確認してください。

## <a name="anchoring-an-experience"></a>エクスペリエンスの固定

前のセクションでは、Azure Spatial Anchors の基礎について学習しました。 キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。 このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。

[Hierarchy]\(階層\) ウィンドウで、**ParentAnchor** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Transform** コンポーネントを次のように構成します。

* **[Scale X]\(X 拡大縮小\)** を 1.1 に変更します
* **[Scale Z]\(Z 拡大縮小\)** を 1.1 に変更します

![ParentAnchor オブジェクトが選択され、配置され、スケーリングされている Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[Rover]** フォルダーの順に移動し、**RoverExplorer_Complete** プレハブをクリックして [Hierarchy]\(階層\) ウィンドウにドラッグし、シーンに追加します。

![新しく追加された RoverExplorer_Complete プレハブが選択されている Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

新しく追加した RoverModule_Complete オブジェクトが [Hierarchy]\(階層\) ウィンドウで選択されたままの状態で、それを **ParentAnchor** オブジェクトにドラッグして、ParentAnchor オブジェクトの子にします。

![RoverExplorer_Complete オブジェクトが ParentAnchor の子として設定されている Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

ここでプロジェクトを再ビルドして、アプリをご利用のデバイスにデプロイすると、サイズ変更したキューブを移動して、Rover エクスプローラー エクスペリエンス全体を再配置できます。

> [!TIP]
> エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界コントロールを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。 このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止を行うため、および単一のデバイスで Azure Spatial Anchors の作成、アップロード、ダウンロードを行うために 必要なさまざまな手順を調べることができるいくつかのボタンについて説明しました。

次のチュートリアルでは、アプリを再起動した後でも取得できるように、Azure アンカー ID を HoloLens 2 に保存する方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせを行う方法について学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル:3.Azure Spatial Anchors の保存、取得、および共有](mr-learning-asa-03.md)
