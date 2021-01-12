---
title: MRTK のチュートリアル - 2. プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) 用に Unity プロジェクトを構成する方法と、それを HoloLens 2 に配置する方法について説明します。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859531"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. プロジェクトの初期化と最初のアプリケーションの配置

## <a name="overview"></a>概要

このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。 また、Visual Studio で基本的な Unity シーンを構成およびビルドし、HoloLens 2 に配置する方法についても説明します。 HoloLens 2 に配置すると、HoloLens によって認識されたサーフェスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。

## <a name="objectives"></a>目標

* HoloLens 開発用に Unity を構成する方法について学習する。
* アプリをビルドして HoloLens に配置する方法について学習する。
* HoloLens 2 デバイスで空間マッピング メッシュ、ハンド メッシュ、フレームレート カウンターを体験する。

## <a name="creating-the-unity-project"></a>Unity プロジェクトの作成

1. **Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択してから、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。

![[New]\(新規\) ボタンの下矢印が強調表示されている Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

2. ドロップダウン メニューで、「[前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity のバージョンを選択します。

![Unity のバージョンを選択する](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。

3. **[Create a new project]\(新規プロジェクトの作成\)** ウィンドウで、次の手順を実行します。

    * **[Templates]\(テンプレート\)** が **[3D]** に設定されていることを確認します。
    * **[Project Name]\(プロジェクト名\)** ボックスに、プロジェクトの適切な名前 (「MRTK Tutorials」など) を入力します。
    * **[Location]\(保存先\)** の横にある 3 つのドット ボタンをクリックして、プロジェクトを保存するフォルダーに移動します。

> [!CAUTION]
> Windows で作業している場合は、255 文字の MAX_PATH 制限があります。 そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。

    * **[作成]** ボタンをクリックします。 すると、新しい Unity プロジェクトが作成されて起動します。

![[Create a new project]\(新規プロジェクトの作成\) ウィンドウが設定された Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

ステータス バーに進行状況が表示されます。

![プロジェクトの作成状態を表示する Unity の進行状況バー](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>ビルド プラットフォームを切り替える

1. メニュー バーで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択します。

![Unity の [Build Settings...]\(ビルド設定...\) メニュー パス](images/mr-learning-base/base-02-section2-step1-1.png)

2. **[Build Settings]\(ビルド設定\)** ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。

![UWP が選択されてプラットフォームがスタンドアロンから切り替えられている Unity の [Build Settings]\(ビルド設定\) ウィンドウ](images/mr-learning-base/base-02-section2-step1-2.png)

3. Unity でプラットフォームの切り替えが完了するのを待ってから、 **[Build Settings]\(ビルド設定\)** ウィンドウを閉じます。

## <a name="importing-the-textmeshpro-essential-resources"></a>TextMeshPro の重要なリソースをインポートする

TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。 プロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。

1. メニュー バーで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択します。

![Unity の [Import TMP Essential Resources]\(TMP の重要なリソースをインポート\) メニュー パス](images/mr-learning-base/base-02-section3-step1-1.png)

2. **[Import Unity Package]\(Unity パッケージのインポート\)** ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認したら、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

![Unity の TMP の重要なリソース インポート ウィンドウ](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit をインポートする

1. Unity カスタム パッケージをダウンロードします。

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. メニュー バーで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** の順に選択します。
3. **[Import Package...]\(パッケージのインポート...\)** ダイアログで、ダウンロードしたパッケージの保存先に移動し、そのパッケージを選択して、 **[Open]\(開く\)** ボタンをクリックします。
4. **[Import Unity Package]\(Unity パッケージのインポート\)** ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認したら、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。

## <a name="selecting-mrtk-and-project-settings"></a>MRTK とプロジェクトの設定を選択する

Unity によって前のセクションからのパッケージのインポートが完了すると、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが表示されます。 表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。

![Unity の [Configure Unity Project]\(Unity プロジェクトの構成\) メニュー パス](images/mr-learning-base/base-02-section5-step1-1.png)

1. **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウで、必要に応じて **[Modify Configurations]\(構成の変更\)** セクションを展開し、すべてのオプションが選択されていることを確認します。

![[Modify Configurations]\(構成の変更\) が表示されている Unity の [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウ](images/mr-learning-base/base-02-section5-step1-2.png)

2. 設定を適用するには、 **[Apply]\(適用\)** ボタンをクリックします。

![MRTK の [Apply]\(適用\) ボタン](images/mr-learning-base/apply.png)

> [!NOTE]
> 新しいシステムはこのチュートリアル シリーズに対して[推奨される Unity および MRTK のバージョン](mr-learning-base-01.md#prerequisites)と完全には互換性がないため、新しい XR プラグイン システムではなく、Unity の組み込みのレガシ XR を使用しています。 組み込みの XR は非推奨であることを示す警告が表示されても、無視してかまいません。

> [!TIP]
> MRTK の既定の設定の適用はオプションですが、一部の推奨される Unity 設定を構成するのに役立つので強く推奨されます。
>
> * [Enable legacy XR]\(レガシ XR を有効にする\): プロジェクトの VR を有効にします。
> * [Set Single Pass Instanced rendering path]\(単一パスのインスタンス化レンダリング パスを設定する\): 同じ描画呼び出しで両方の目のレンダリング パイプラインを実行することにより、グラフィックスのパフォーマンスを向上させます。 このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[単一パス インスタンス化レンダリング](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)」セクションを参照してください。
> * [Set default Spatial Awareness layer]\(既定の空間認識レイヤーを設定する\): 空間認識という名前の Unity レイヤーを作成し、空間認識メッシュにこのレイヤーを使用するように MRTK を構成します。 Unity レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。

3. メニュー バーで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** の順に選択します。

4. **[Project Settings...]\(プロジェクト設定...\)** ウィンドウで、 **[Player]\(プレイヤー\)** を選択し、 **[XR Settings]\(XR 設定\)** ドロップダウンをクリックして、 **[Virtual Reality Supported]\(仮想現実のサポート\)** の横にあるチェックボックスをオンにします。

![[Virtual Reality Supported]\(仮想現実のサポート\) が表示されている Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-2.png)

これにより、Windows Mixed Reality SDK がインポートされます。

![[Virtual Reality SDKs]\(仮想現実 SDK\) が表示されている Unity の XR 設定](images/mr-learning-base/mixed-reality-sdk.png)

Unity によって Windows Mixed Reality SDK のインポートが完了すると、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが再び表示されます。 表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、ウィンドウを開きます。

5. **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウで、 **[Audio spatializer]\(オーディオ スペーシャライザー\)** ドロップダウンをクリックし、 **[MS HRTF Spatializer]\(MS HRTF スペーシャライザー\)** を選択します。

![[Audio spatializer]\(オーディオ スペーシャライザー\) オプションが表示されたプロジェクト設定](images/mr-learning-base/base-02-section5-step2-3.png)

6. **[適用]** をクリックします。 これにより、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが閉じます。

    > [!TIP]
    > Audio Spatializer プロパティの設定はオプションですが、プロジェクトでのオーディオ エクスペリエンスが向上する場合があります。 MS HRTF Spatializer に設定した場合、Unity の AudioSource.spatialize プロパティが有効になっていると、この Spatializer プラグインが使用されます。 このトピックの詳細については、立体オーディオのチュートリアルに関するページを参照してください。

7. **[Project Settings]\(プロジェクト設定\)** ウィンドウで、 **[Depth Format]\(深度形式\)** ドロップダウンをクリックして、 **[16-bit depth]\(16 ビット深度\)** を選択します。

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="[16-bit depth]\(16 ビット深度\) が選択された Unity の XR 設定":::

    > [!TIP]
    > 深度形式を 16 ビットに減らすことはオプションですが、プロジェクトでのグラフィックス パフォーマンスの向上につながる可能性があります。 このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[深度バッファー共有 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens)」セクションを参照してください。

8. **[Publishing Settings]\(公開設定\)** ドロップダウンをクリックし、 **[Package name]\(パッケージ名\)** ボックスに適切な名前 (「MRTK-Tutorials-Getting-Started」など) を入力します。

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="パッケージ名が構成されている Unity の公開設定":::

    **パッケージ名と製品名**

    - 'パッケージ名' は、アプリの一意の識別子です。 以前にインストールしたアプリが上書きされないようにするため、アプリを配置する前にこの識別子を作成する必要があります。
    - '製品名' は、HoloLens の [スタート] メニューに表示される名前です。 名前の前にアンダースコアを追加すると、並べ替えの先頭に表示されるので、開発中にアプリを見つけやすくなります。

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="製品名が構成されている Unity のプロジェクト設定":::

9. **[Project Settings]\(プロジェクト設定\)** ウィンドウを閉じます。

## <a name="creating-and-configuring-the-scene"></a>シーンを作成して構成する

1. メニュー バーで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択します。
2. シーンに MRTK を追加するには、Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択します。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity の [Add to Scene and Configure...]\(シーンに追加して構成する...\) メニュー パス":::

3. **[Hierarchy]\(階層\)** ウィンドウで、 **[MixedRealityToolkit]** が選択されていることを確認します。

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="[MixedRealityTookit] が選択されていることを確認する":::

4. **[Inspector]\(インスペクター\)** ウィンドウの **[MixedRealityToolkit]** セクションで、構成プロファイルが **[DefaultMixedRealityToolkitConfigurationProfile]** に設定されていることを確認します。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="[DefaultMixedRealityTookitConfigurationProfile] が選択された Unity の MixedRealityToolkit コンポーネント":::

    > [!IMPORTANT]
    > 通常、HoloLens 向けの開発時には DefaultHoloLens2ConfigurationProfile を使用します。 ただし、このチュートリアルでは DefaultMixedRealityToolkitConfigurationProfile を使用します。 次のチュートリアル (「[MRTK プロファイルの構成](mr-learning-base-03.md)」) では、DefaultHoloLens2ConfigurationProfile に変更します。

5. メニュー バーで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** の順に選択します。
6. **[Save Scene]\(シーンの保存\)** ダイアログで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動します。 **[File name]\(ファイル名\)** ボックスで、シーンに適切な名前 (「\_GettingStarted\_」など) を指定し、 **[Save]\(保存\)** ボタンをクリックします。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity のシーン保存の [Save]\(保存\) プロンプト ウィンドウ":::

## <a name="building-and-deploying-to-your-hololens-2"></a>HoloLens 2 へのビルドと配置

> デバイスにビルドする前に、次のことを確認します。
- デバイスが開発者モードである。
- デバイスが開発用コンピューターとペアリングされている。 ペアリングされていない場合、ビルド プロセス中に、次のダイアログ ボックスが Visual Studio に表示されます。

![ペアリング デバイスの PIN の入力](images/mr-learning-base/pin-request.png)

 これらの手順の詳細については、「[Visual Studio を使用した配置とデバッグ](../../platform-capabilities-and-apis/using-visual-studio.md)」を参照してください。

1. メニュー バーで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択します。
2. **[Build Settings]\(ビルドの設定\)** ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、現在のシーンを **[Scenes in Build]\(ビルド内のシーン\)** リストに追加します。

![現在のシーンを [Scenes in Build]\(ビルド内のシーン\) リストに追加](images/mr-learning-base/base-02-section7-step1-1.png)

3. **[ビルド]** ボタンをクリックします。

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="[ビルド] ボタンをクリックします。":::

4. **[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\)** ダイアログで、ビルドを格納するのに適した保存先を選択します (たとえば、"MRTK Tutorials" フォルダーに "Builds" フォルダーを作成することもできます)。 新しいフォルダーを作成して、適切な名前 ("GettingStarted" など) を指定し、そのフォルダーを選択します。次に **[Select Folder]\(フォルダーの選択\)** ボタンをクリックして、ビルド プロセスを開始します。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="ビルド フォルダーが表示されている Unity の [Build]\(ビルド\) ウィンドウ":::

    ステータス バーが表示され、ビルドの進行状況が表示されます。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="進行中の Unity のビルド プロセス":::

    > [!TIP]
    > また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。

5. ビルド プロセスが完了したら、エクスプローラーで、ビルドを格納した保存先に移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="新しく作成された Visual Studio のソリューション ファイルが選択されたエクスプローラー":::

    > [!NOTE]
    > Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。

6. **[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。

    > [!TIP]
    > HoloLens (第 1 世代) に配置する場合は、**x86** アーキテクチャを選択します。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="HoloLens 2 に配置するように構成された Visual Studio":::

    > [!NOTE]
    > HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。 ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。 推奨される回避策は、ARM64 用にビルドすることです。 それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。

    > [!NOTE]
    > ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。 これを行うには、ソリューション エクスプローラーで [YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックして、 **[スタートアップ プロジェクトに設定]** を選択します。

7. HoloLens をコンピューターに接続し、次のいずれかの操作を行います。
- アプリをビルドし、HoloLens に配置して、Visual Studio デバッガーがアタッチされていない状態で自動的に起動するには、メニュー バーで、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択します。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio の [デバッグなしで開始] メニュー パス":::

- アプリを HoloLens にビルドして配置はするものの、自動的に起動しないようにするには、メニュー バーで **[ビルド] > [ソリューションの配置]** の順に選択します。

    > [!NOTE]
    >アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。 アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。 たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。

## <a name="congratulations"></a>結論

これで、最初の HoloLens アプリが展開されました。 手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。 さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。 これらの機能は、MRTK に含まれている基本的なもののほんの一部です。 次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。

> [!div class="nextstepaction"]
> [次のチュートリアル:3. MRTK プロファイルの構成](mr-learning-base-03.md)
