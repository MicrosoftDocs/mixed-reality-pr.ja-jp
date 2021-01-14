---
title: Photon Unity Networking の設定
description: このコースを完了すると、HoloLens 2 Mixed Reality アプリケーションで Photon Unity Network を実装する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, マルチユーザー機能, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, PUN
ms.localizationpriority: high
ms.openlocfilehash: 8bf8d440cb47d817514e34c98ac45f34f495c2bb
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007302"
---
# <a name="2-setting-up-photon-unity-networking"></a>2.Photon Unity Networking の設定

このチュートリアルでは、Photon Unity Networking (PUN) を使用して共有エクスペリエンスの作成準備をします。 PUN アプリの作成方法、PUN アセットを Unity プロジェクトにインポートする方法、Unity プロジェクトを PUN アプリに接続する方法について説明します。

## <a name="objectives"></a>目標

* PUN アプリを作成する方法を学習する
* PUN アセットを探してインポートする方法を学習する
* Unity プロジェクトを PUN アプリに接続する方法を学習する

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

最初に、「[プロジェクトの初期化と最初のアプリケーションの配置](mr-learning-base-02.md)」に従います (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける
2. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity プロジェクトを構成する](mr-learning-base-02.md#selecting-mrtk-and-project-settings)
6. [シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *MultiUserCapabilities* などの適切な名前を付ける

次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の指示に従い、次の作業を行います。

1. **MRTK 構成プロファイル** を **DefaultHoloLens2ConfigurationProfile** に変更します
1. **空間認識メッシュ表示オプション** を **[Occlusion]\(オクルージョン\)** に変更します

## <a name="enabling-additional-capabilities"></a>その他の機能を有効にする

Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。

![[Player]\(プレーヤー\) 設定が表示された Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、上の「[Unity プロジェクトを構成する](mr-learning-base-02.md#selecting-mrtk-and-project-settings)」手順で有効にした **InternetClient**、**Microphone**、**SpatialPerception**、**GazeInput** の機能が有効になっていることを再確認します。

その後、次の追加機能を有効にします。

* **InternetClientServer** 機能
* **PrivateNetworkClientServer** 機能

![[Capabilities]\(機能\) 設定が表示された Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>組み込みの Unity パッケージのインストール

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。

![AR Foundation が選択されている [Package Manager]\(パッケージ マネージャー\) が表示された Unity](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> 次のセクションでインポートする Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (バージョン 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。

> [!NOTE]
> MultiUserCapabilities チュートリアル アセット パッケージをインポートすると、型または名前空間が存在しないことを示すいくつかの [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) エラーが [Console]\(コンソール\) ウィンドウに表示されます。 これは想定されているものであり、次のセクションで PUN アセットをインポートする際に解決されます。

## <a name="importing-the-pun-assets"></a>PUN アセットをインポートする

Unity メニューで、 **[Window]\(ウィンドウ\)** 、 **[Asset Store]\(アセット ストア\)** の順に選択して [Asset Store]\(アセット ストア\) ウィンドウを開き、Exit Games から **[PUN 2 - FREE]** を検索して選択し、 **[Download]\(ダウンロード\)** ボタンをクリックしてアセット パッケージを自分の Unity アカウントにダウンロードします。

ダウンロードが完了したら、 **[Import]\(インポート\)** ボタンをクリックして [Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。

![[PUN 2 - Free] が表示された [Asset Store]\(アセット ストア\) が表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![PUN 2 のインポート ウィンドウが表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Unity でインポート プロセスが完了したら、[Pun Wizard]\(Pun ウィザード\) ウィンドウが表示されて [PUN Setup]\(PUN 設定\) メニューが読み込まれます。今はこのウィンドウを無視するか、閉じて構いません。

![[PUN Setup]\(PUN 設定\) ウィンドウが表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>PUN アプリケーションの作成

このセクションでは、Photon アカウントを作成し (まだ作成していない場合)、新しい PUN アプリを作成します。

使用したいアカウントが既にある場合は Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">ダッシュボード</a> に移動してサインインします。なければ、 **[こちらから作成してください]** リンクをクリックして手順に従い、新しいアカウントを登録します。

![Photon ログイン ページ](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

サインインしたら、 **[Create a New App]\(新しいアプリの作成\)** ボタンをクリックします。

![Photon ダッシュボードの開始ページ](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

[Create a New Application]\(新しいアプリケーションの作成\) ページで、次の値を入力します。

* [Photon Type]\(Photon の種別\) には、[PUN] を選択します
* [Name]\(名前\) には、適切な名前 (_MRTK チュートリアル_ など) を入力します
* [Description]\(説明\) には、必要に応じて適切な説明を入力します
* "URL" フィールドは空のままにします

**[Create]\(作成する\)** をクリックして新しいアプリを作成します。

![Photon のアプリケーションの作成ページ](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Photon で作成プロセスが完了すると、新しい PUN アプリがダッシュボードに表示されます。

![Photon のアプリケーション ページ](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Unity プロジェクトを PUN アプリケーションに接続する

このセクションでは、Unity プロジェクトを前のセクションで作成した PUN アプリに接続します。

Photon ダッシュボードで、 **"App ID"(アプリ ID)** フィールドをクリックしてアプリ ID を表示し、クリップボードにコピーします。

![アプリ ID が選択されている Photon アプリケーション ページ](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Photon Unity Networking]**  >  **[PUN Wizard]\(PUN ウィザード\)** を選択して [Pun Wizard]\(Pun ウィザード\) ウィンドウを開き、 **[Setup Project]\(プロジェクトの設定\)** ボタンをクリックして [PUN Setup]\(PUN 設定\) メニューを開いて次のように構成します。

* **"AppId or Email"(アプリ ID またはメール)** フィールドで、前のステップでコピーした PUN アプリ ID を貼り付けます

**[Setup Project]\(プロジェクトの設定\)** ボタンをクリックしてアプリ ID を適用します。

![アプリ ID が入力された [PUN Setup]\(PUN 設定\) が表示された Unity](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Unity で PUN 設定プロセスが完了すると、[PUN Setup]\(PUN 設定\) メニューに **[Done!]\(完了\)** というメッセージが表示され、 [Project]\(プロジェクト\) ウィンドウで **PhotonServerSettings** アセットが自動的に選択され、そのプロパティが [Inspector]\(インスペクター\) ウィンドウに表示されます。

![[Setup Project]\(プロジェクトの設定\) が適用された [PUN Setup]\(PUN 設定\) が表示された Unity](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>結論

PUN アプリを作成して、これを Unity プロジェクトに接続できました。 次の手順では、他のユーザーとの接続を許可して複数のユーザーが互いを見られるようにします。

> [!div class="nextstepaction"]
> [次のチュートリアル:3.複数ユーザーの接続](mr-learning-sharing-03.md)
