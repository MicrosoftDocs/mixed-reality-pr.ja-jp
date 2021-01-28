---
title: プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) 用に Unity プロジェクトを構成する方法と、それを HoloLens 2 に配置する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4d82d0974a0a797e7f8d2de2d4943666f7d32a4f
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635510"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. プロジェクトの初期化と最初のアプリケーションの配置

このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。 また、Visual Studio で基本的な Unity シーンを構成およびビルドし、HoloLens 2 に配置する方法についても説明します。 HoloLens 2 に配置すると、HoloLens によって認識されたサーフェスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。

## <a name="objectives"></a>目標

* HoloLens 開発用に Unity を構成する方法について学習する
* アプリをビルドして HoloLens に配置する方法について学習する
* HoloLens 2 デバイスで空間マッピング メッシュ、ハンド メッシュ、フレームレート カウンターを体験する

## <a name="creating-the-unity-project"></a>Unity プロジェクトの作成

**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。

![[New]\(新規\) ボタンが強調表示されている Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

「[前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity の **バージョン** を、ドロップダウンで選択します。

![Unity Hub と新しいバージョン セレクター ドロップダウン](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。

[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。

* **[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します
* "_MRTK チュートリアル_" など、適切な **[Project Name]\(プロジェクト名\)** を入力します
* プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、_D:\MixedRealityLearning_ など
* **[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します

![[Create a new project]\(新規プロジェクトの作成\) ウィンドウが設定された Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Windows で作業している場合は、255 文字の MAX_PATH 制限があります。 そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。

Unity によってプロジェクトが作成されるまで待ちます。

![新しいプロジェクトの作成が進行中の Unity](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>ビルド プラットフォームを切り替える

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。

![Unity の [Build Settings...]\(ビルド設定...\) メニュー パス](images/mr-learning-base/base-02-section2-step1-1.png)

[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。

![UWP が選択されてプラットフォームがスタンドアロンから切り替えられている Unity の [Build Settings]\(ビルド設定\) ウィンドウ](images/mr-learning-base/base-02-section2-step1-2.png)

Unity がプラットフォームの切り替えを完了するまで待ちます。

![プラットフォームの切り替えが進行中の Unity](images/mr-learning-base/base-02-section2-step1-3.png)

Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。

![閉じるアイコンが強調表示されている Unity のビルド ウィンドウ](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>TextMeshPro の重要なリソースをインポートする

Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択して、[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。

![Unity の [Import TMP Essential Resources]\(TMP の重要なリソースをインポート\) メニュー パス](images/mr-learning-base/base-02-section3-step1-1.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![Unity の TMP の重要なリソース インポート ウィンドウ](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。 ご自分のプロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。

## <a name="importing-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit をインポートする

Unity カスタム パッケージをダウンロードします。

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

Unity メニューで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** を選択して [Import package...]\(パッケージのインポート...\) ウィンドウを開きます。

![Unity のインポートの [Custom Package...]\(カスタム パッケージ...\) メニュー パス](images/mr-learning-base/base-02-section4-step1-1.png)

[Import package...]\(パッケージのインポート...\) ウィンドウで、ダウンロードした **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** を選択し、 **[Open]\(開く\)** ボタンをクリックします。

![Unity のカスタム パッケージのインポートの [Open]\(開く\) プロンプト ウィンドウ](images/mr-learning-base/base-02-section4-step1-2.png)

[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![Unity MRTK Foundation インポート ウィンドウ](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Unity プロジェクトを構成する

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. MRTK プロジェクト コンフィギュレーター設定を適用する

Unity によって前のセクションからのパッケージのインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。 表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。

![Unity の [Configure Unity Project]\(Unity プロジェクトの構成\) メニュー パス](images/mr-learning-base/base-02-section5-step1-1.png)

[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、他のすべてのオプションを確実にオンにしてから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。

![[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> MRTK の既定の設定の適用はオプションですが、一部の推奨される Unity 設定を構成するのに役立つので強く推奨されます。

> * [Set Single Pass Instanced rendering path]\(単一パスのインスタンス化レンダリング パスを設定する\): 同じ描画呼び出しで両方の目のレンダリング パイプラインを実行することにより、グラフィックスのパフォーマンスを向上させます。 このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[単一パス インスタンス化レンダリング](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)」セクションを参照してください。
> * [Set default Spatial Awareness layer]\(既定の空間認識レイヤーを設定する\): 空間認識という名前の Unity レイヤーを作成し、空間認識メッシュにこのレイヤーを使用するように MRTK を構成します。 Unity レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。

### <a name="2-configure-additional-project-settings"></a>2.追加のプロジェクト設定を構成する

Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。

![Unity の [Project Settings...]\(プロジェクト設定...\) メニュー パス](images/mr-learning-base/base-02-section5-step2-1.png)

[Project Settings]\(プロジェクトの設定\) ウィンドウで、 **[XR Plug-in Management]\(XR プラグイン管理\)**  >  **[Install XR Plug-in Management]\(XR プラグイン管理のインストール\)** を選択して、XR プラグイン管理をインストールします。

![パッケージ名が構成されている Unity の公開設定](images/mr-learning-base/base-02-section5-step2-2.png)

Unity による XR プラグイン管理のインストールが完了した後。 ユニバーサル Windows プラットフォームの設定になっていることを確認し、[Initialize XR on Startup]\(起動時に XR を初期化する\) をオンにします。

![Unity 構成 XR プラグインの管理](images/mr-learning-base/base-02-section5-step2-3.png)

[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** の順に選択し、[ **+** ] アイコンをクリックします。Windows Mixed reality を選択して Windows Mixed Reality SDK を追加します。

![Windows Mixed Reality SDK の追加が選択された Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-4.png)

Unity によって Windows Mixed Reality SDK のインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが再び表示されます。 そうならない場合は、Unity メニューを使用してそれを開きます。

[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Audio Spatializer]** ドロップダウンを使用して **[MS HRTF Spatializer]** を選択してから、 **[Apply]\(適用\)** ボタンをクリックしてこの設定を適用します。

![Windows Mixed Reality SDK の追加が選択された Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>Audio Spatializer プロパティの設定はオプションですが、プロジェクトでのオーディオ エクスペリエンスが向上する場合があります。 MS HRTF Spatializer に設定した場合、Unity の AudioSource.spatialize プロパティが有効になっていると、この Spatializer プラグインが使用されます。 このトピックの詳細については、<a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">立体オーディオのチュートリアル</a>に関するページを参照してください。

[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択してから、 **[Depth Format]\(深度形式\)** ドロップダウンを使用して **[16-bit depth]\(16 ビット深度\)** を選択します。

![Unity で 16 ビット深度を有効にする](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> 深度形式を 16 ビットに減らすことはオプションですが、プロジェクトでのグラフィックス パフォーマンスの向上につながる可能性があります。 このトピックの詳細については、MRTK の「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">パフォーマンス</a>」ドキュメントの「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度バッファー共有 (HoloLens)</a>」セクションを参照してください。

[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開の設定\)** の順に選択してから、 **[Package name]\(パッケージ名\)** フィールドに適切な名前 (たとえば _MRTKTutorials-GettingStarted_) を入力します。

![パッケージ名が構成されている Unity の公開設定](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> 'パッケージ名' は、アプリの一意の識別子です。 以前にインストールしたアプリが上書きされないように、アプリを配置する前にこの識別子を変更する必要があります。

> [!TIP]
> '製品名' は、HoloLens の [スタート] メニューに表示される名前です。 開発中にアプリを見つけやすくするには、名前の前にアンダースコアを追加し、上部にくるように並べ替えます。

## <a name="creating-and-configuring-the-scene"></a>シーンを作成して構成する

Unity メニューで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択して新しいシーンを作成します。

![Unity の [New Scene]\(新しいシーン\) メニュー パス](images/mr-learning-base/base-02-section6-step1-1.png)

Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、MRTK を現在のシーンに追加します。

![Unity の [Add to Scene and Configure...]\(シーンに追加して構成する...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-2.png)

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択したままとし、[Inspector]\(インスペクター\) ウィンドウで、**MixedRealityToolkit** 構成プロファイルが **DefaultMixedRealityToolkitConfigurationProfile** に設定されていることを確認します。

![DefaultMixedRealityTookitConfigurationProfile が選択された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-02-section6-step1-3.png)

Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。

![Unity の [Save As...]\(名前を付けて保存...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-4.png)

[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、_GettingStarted_)、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。

![Unity のシーン保存の [Save]\(保存\) プロンプト ウィンドウ](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>HoloLens 2 デバイス用にアプリケーションをビルドする

### <a name="1-build-the-unity-project"></a>1.Unity プロジェクトのビルド

Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。

[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。

![UWP が選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-1.png)

[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。

![[フォルダーの選択] プロンプト ウィンドウが表示されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-2.png)

Unity がビルド処理を完了するまで待ちます。

![ビルド処理が進行中の Unity](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.アプリのビルドと配置

ビルド処理が完了すると、お客様がビルドを格納した場所を開くように Unity から Windows ファイル エクスプローラーに指示が出されます。 フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。

![新しく作成された Visual Studio ソリューションが選択された Windows エクスプローラー](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。

**[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。

![HoloLens 2 に配置するように構成された Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> HoloLens (第 1 世代) に配置する場合は、**x86** アーキテクチャを選択します。

> [!NOTE]
> HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。 ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。 推奨される回避策は、ARM64 用にビルドすることです。 それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。

> [!NOTE]
> ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。 それを行うには、ソリューション エクスプローラーで、[YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックし、 **[スタートアップ プロジェクトに設定]** を選択します。

ご利用のコンピューターに HoloLens を接続し、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択して、ご利用のデバイス用にビルドして配置します。

![Visual Studio の [デバッグなしで開始] メニュー パス](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。 この両方のステップを完了するには、[こちらの手順](../../platform-capabilities-and-apis/using-visual-studio.md)に従います。

> [!TIP]
> また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。

[デバッグなしで開始] を使用すると、Visual Studio デバッガーがアタッチされていない状態でも、ご利用のデバイス上でアプリが自動的に起動します。

アプリを自動的に起動せずに、ご利用のデバイスに配置するには、 **[ビルド] > [ソリューションの配置]** の順に選択します。

> [!NOTE]
>アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。 アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。 たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。

## <a name="congratulations"></a>結論

これで、最初の HoloLens アプリが展開されました。 手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。 これらの機能は、MRTK に含まれている基本的なもののほんの一部です。 次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。

> [!div class="nextstepaction"]
> [次のチュートリアル:3. MRTK プロファイルの構成](mr-learning-base-03.md)