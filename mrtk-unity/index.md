---
title: MRTK-Unity 開発者向けドキュメント
description: Unity 用 Mixed Reality Toolkit について説明します。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 開発, MRTK
ms.openlocfilehash: 3ac16a1aae6681ddd7e144679b76b4d2b778306f
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237253"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit とは

![Mixed Reality ツールキット](features/images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity は、一連のコンポーネントと機能を提供する Microsoft 主導のプロジェクトで、Unity でクロスプラットフォームの MR アプリの開発時間を短縮するために使用されます。 その機能の一部を次に示します。

* **空間操作および UI 用のクロスプラットフォーム入力システムと構成要素** が提供されます。
* エディター内シミュレーションを通じて **プロトタイプの迅速な作成** を実現し、変更を即座に確認できるようになります。
* 開発者がコア コンポーネントを交換できる **拡張可能なフレームワーク** として動作します。
* 次のような **幅広い範囲のプラットフォームをサポート** します
  * OpenXR (Unity 2020.2 以降)
    * Microsoft HoloLens 2
    * Windows Mixed Reality ヘッドセット
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Windows Mixed Reality ヘッドセット
  * Oculus (Unity 2019.3 以降)
    * Oculus Quest
  * OpenVR
    * Windows Mixed Reality ヘッドセット
    * HTC Vive
    * Oculus Rift
  * Ultraleap ハンド トラッキング
  * iOS や Android などのモバイル デバイス

## <a name="getting-started-with-mrtk"></a>MRTK の概要

Unity での MRTK または Mixed Reality 開発が初めての場合は、必要なツールをインストールした後、HoloLens 2 チュートリアル シリーズに従うことをお勧めします。

> [!div class="nextstepaction"]
> [ツールのインストール](install-the-tools.md)

> [!div class="nextstepaction"]
> [HoloLens 2 チュートリアル シリーズ](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

内部的なしくみを確認したい場合は、次を参照してください。
> [!div class="nextstepaction"]
> [GitHub で MRTK を調べる](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>ドキュメント

| [![リリース ノート](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[リリース ノート](release-notes/mrtk-26-release-notes.md)| [![MRTK の概要](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[MRTK の概要](architecture/overview.md)|[![API リファレンス](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[API リファレンス](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>ビルドの状態

| [Branch]\(ブランチ) | CI の状態 | ドキュメントの状態 |
|---|---|---|
| `mrtk_development` |[![CI の状態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![ドキュメントの状態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>機能領域

:::row:::
    :::column:::
       [![入力システム](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[入力システム](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![ハンド トラッキング (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[ハンド トラッキング <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![視線追跡 (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[視線追跡 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![プロファイル](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md) **[プロファイル](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![ハンド トラッキング (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[ハンド トラッキング <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![UI コントロール](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[UI コントロール](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![ソルバー](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[ソルバー](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![マルチシーン マネージャー](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[マルチシーン<br/> マネージャー](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![空間認識](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間 <br/> 認識](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![診断ツール](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[診断 <br/> ツール](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![MRTK 標準シェーダー ビュー](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[MRTK 標準シェーダー ビューの例](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![音声認識 & ディクテーション](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[音声認識](features/input/speech.md)<br/> & [ディクテーション](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![境界システム](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[境界 <br/>システム](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![エディター内シミュレーション](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md) **[エディター内 <br/> シミュレーション](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![試験的な機能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[試験的な <br/> 機能](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>UX 構成要素

:::row:::
    :::column:::
       [![ボタン](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[ボタン](features/ux-building-blocks/button.md)**<br>
        HoloLens 2 の多関節ハンドを含む各種入力方法がサポートされているボタン コントロール
    :::column-end:::
    :::column:::
        [![境界コントロール](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[境界コントロール](features/ux-building-blocks/bounds-control.md)**<br>
        3D 空間内のオブジェクトを操作するための標準 UI
    :::column-end:::
    :::column:::
        [![オブジェクト マニピュレーター](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[オブジェクト マニピュレーター](features/ux-building-blocks/object-manipulator.md)**<br>
        片手または両手でオブジェクトを操作するためのスクリプト
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![スレート](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[スレート](features/ux-building-blocks/slate.md)**<br>
        多関節ハンド入力によるスクロールがサポートされている 2D スタイルの平面
    :::column-end:::
    :::column:::
        [![システム キーボード](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[システム キーボード](features/ux-building-blocks/system-keyboard.md)**<br>
        Unity でシステム キーボードを使用するサンプル スクリプト
    :::column-end:::
    :::column:::
        [![対話可能](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[対話可能](features/ux-building-blocks/interactable.md)**<br>
        視覚的な状態とテーマのサポートを使用してオブジェクトを対話型にするためのスクリプト
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![ソルバー](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[ソルバー](features/ux-building-blocks/solvers/solver.md)**<br>
        追従、本体ロック、ビュー サイズの固定、表面吸着など、さまざまなオブジェクトの配置動作
    :::column-end:::
    :::column:::
        [![オブジェクト コレクション](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[オブジェクト コレクション](features/ux-building-blocks/object-collection.md)**<br>
        多数のオブジェクトを 3 次元形状で並べるためのスクリプト
    :::column-end:::
    :::column:::
        [![ツールヒント](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[ツールヒント](features/ux-building-blocks/tooltip.md)**<br>
        モーション コントローラーとオブジェクトのラベル付けに使用できる、柔軟なアンカーおよびピボット システムを備えた注釈 UI
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![スライダー](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[スライダー](features/ux-building-blocks/sliders.md)**<br>
        直接のハンド トラッキング操作がサポートされている、値調整のためのスライダー UI
    :::column-end:::
    :::column:::
        [![MRTK 標準シェーダー](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 標準シェーダー](features/rendering/mrtk-standard-shader.md)**<br>
        MRTK の標準シェーダーでは、さまざまな Fluent デザイン要素とパフォーマンスがサポートされています
    :::column-end:::
    :::column:::
        [![ハンド メニュー](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[ハンド メニュー](features/ux-building-blocks/hand-menu.md)**<br>
        ハンド制約ソルバーを使用した、クイック アクセス用のハンドロック UI
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![アプリ バー](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[アプリ バー](features/ux-building-blocks/app-bar.md)**<br>
        境界コントロールの手動アクティブ化のための UI
    :::column-end:::
    :::column:::
        [![ポインター](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[ポインター](features/input/pointers.md)**<br>
        さまざまな種類のポインターについて説明します
    :::column-end:::
    :::column:::
        [![指先の視覚化](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[指先の視覚化](features/ux-building-blocks/fingertip-visualization.md)**<br>
        直接操作の信頼度を向上させる、指先の視覚的アフォーダンス
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![近くのメニュー](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[近くのメニュー](features/ux-building-blocks/near-menu.md)**<br>
        近くの対話式操作のための移動メニュー UI
    :::column-end:::
    :::column:::
        [![空間認識の概要](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間認識ビュー](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        ホログラフィック オブジェクトが物理環境と相互作用するようにする
    :::column-end:::
    :::column:::
        [![音声コマンド](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[音声コマンド](features/input/speech.md)**<br>
        音声入力を統合するためのスクリプトと例
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![進行状況インジケーター](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[進行状況インジケーター](features/ux-building-blocks/progress-indicator.md)**<br>
        データの処理または操作を伝えるための視覚的インジケーター
    :::column-end:::
    :::column:::
        [![ダイアログ](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[ダイアログ](features/ux-building-blocks/dialog.md)**<br>
        ユーザーの確認または同意を求めるための UI
    :::column-end:::
    :::column:::
        [![ハンド コーチ](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[ハンド コーチ](features/ux-building-blocks/hand-coach.md)**<br>
        ジェスチャが学習されていない場合にユーザーをガイドするのに役立つコンポーネント
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![ハンド物理サービス](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[ハンド物理サービス [試験段階]](features/experimental/hand-physics-service.md)**<br>
        ハンド物理サービスによって、剛体の衝突イベントおよび多関節ハンドとの対話が可能になります
    :::column-end:::
    :::column:::
        [![スクロール可能コレクション](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[スクロール可能コレクション](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        3D オブジェクトがネイティブでスクロールされるオブジェクト コレクション
    :::column-end:::
    :::column:::
        [![ドック](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[ドック [試験段階]](features/experimental/dock.md)**<br>
        ドックを使用すると、事前に定義された位置にオブジェクトを出し入れできます
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![視線追跡: ターゲット選択](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[視線追跡: ターゲット選択](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        視線、音声、ハンドの入力を組み合わせて、シーン全体からホログラムをすばやく簡単に選択する
    :::column-end:::
    :::column:::
        [![視線追跡: ナビゲーション](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[視線追跡: ナビゲーション](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        視線に基づいてテキストを自動でスクロールしたり、フォーカスされたコンテンツをなめらかに拡大したりする方法について説明します
    :::column-end:::
    :::column:::
        [![視線追跡: ヒート マップ](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[視線追跡: ヒート マップ](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        アプリ内でユーザーが見ていたもののログ記録、読み込み、視覚化を行う例
    :::column-end:::
:::row-end:::

## <a name="tools"></a>［ツール］

|  [![最適化ウィンドウ](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [最適化ウィンドウ](features/tools/optimize-window.md) | [![依存関係ウィンドウ](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [依存関係ウィンドウ](features/tools/dependency-window.md) | ![ビルド ウィンドウ](features/images/MRTK_Icon_BuildWindow.png) ビルド ウィンドウ | [![入力記録](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [入力記録](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Mixed Reality プロジェクトの構成を自動化してパフォーマンスを最適化します | アセット間の依存関係を分析し、使用されていないアセットを特定します |  Mixed Reality アプリケーションのエンド ツー エンド ビルド プロセスを構成および実行します | エディターで頭の移動とハンド トラッキングのデータを記録および再生します |

## <a name="example-scenes"></a>シーンの例

[こちらのシーンの例](features/example-scenes/hand-interaction-examples.md)で、MRTK のさまざまな種類の対話式操作と UI コントロールについて調べます。

[![シーンの例 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK Examples Hub

MRTK Examples Hub により、MRTK の各種シーンの例を試すことができます。
[MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) で "Mixed Reality Toolkit Examples" パッケージを選択することにより、HoloLens (x86)、HoloLens 2 (ARM)、および Windows Mixed Reality イマーシブ ヘッドセット (x64) 向けの事前構築済みアプリ パッケージをダウンロードできます。 [Windows デバイス ポータルを使って HoloLens (第 1 世代) にアプリをインストールする](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)ようにしてください。 HoloLens 2 では、[Microsoft Store アプリから MRTK Examples Hub](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4) をダウンロードしてインストールすることができます。

MRTK のシーン システムとシーン切り替えサービスを使用してマルチシーン ハブを作成する方法の詳細については、[Examples Hub の README ページ](features/example-scenes/example-hub.md)を参照してください。

[![シーンの例ハブ](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>MRTK を使用して作成されたサンプル アプリ

| [![要素の定期的なテーブル](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![銀河エクスプローラー](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Surfaces サンプル アプリ](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) は、MRTK の入力システムと構成要素を使用して HoloLens およびイマーシブ ヘッドセット用のアプリ エクスペリエンスを作成する方法を示す、オープンソースのサンプル アプリです。 移植のストーリーをご覧ください: 「[MRTK v2 を使用して Periodic Table of the Elements アプリを HoloLens 2 に移植する](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)」 |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) は、元は 2016 年 3 月に HoloLens 'Share Your Idea' キャンペーンの一環として開発された、オープンソースのサンプル アプリです。 Galaxy Explorer は、MRTK v2 を使用して、HoloLens 2 の新機能によって更新されました。 次のストーリーをご覧ください: 「[ HoloLens 2 用 Galaxy Explorer の作成](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)」 |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) は HoloLens 2 用のオープンソースのサンプル アプリです。視覚、音声、完全な多関節ハンド トラッキングを使用して、触覚が作られるしくみを調べることができます。 設計と開発の詳しいストーリーについては、Microsoft MR Dev Days のセッション「[Surfaces アプリを使った学習](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)」をご覧ください。 |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Mixed Reality Dev Days 2020 のセッションのビデオ

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| シンプルな MRTK アプリを、最初から最後まで作成する方法についてのチュートリアルです。 対話式操作の概念と MRTK のマルチプラットフォーム機能について説明します。 | 美しい Mixed Reality エクスペリエンスの構築に役立つ、MRTK の UX 構成要素について詳しく説明します。 | パフォーマンス ツール (MRTK および外部ツールの両方) を紹介し、MRTK 標準シェーダーの概要について説明します。 |

その他のセッション ビデオについては、[Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) に関する記事を参照してください。

## <a name="engage-with-the-community"></a>コミュニティに参加する

* [Slack](https://holodevelopers.slack.com/) で MRTK に関する会話に参加します。 [自動招待センダー](https://holodevelopersslack.azurewebsites.net/)を使用して Slack コミュニティに参加することができます。

* [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) で、**MRTK** タグを使用して MRTK の使用に関する質問をします。

* MRTK コード内に破損を見つけた場合は、[既知のイシュー](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)を検索するか、[新しいイシュー](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)を報告します。

* MRTK への投稿に関する質問については、slack の [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) チャンネルにアクセスしてください。

このプロジェクトは、「[Microsoft のオープン ソースの倫理規定](https://opensource.microsoft.com/codeofconduct/)」を採用しています。
詳細については、[倫理規定の FAQ](https://opensource.microsoft.com/codeofconduct/faq/) のページを参照してください。また、追加の質問やコメントがある場合は [opencode@microsoft.com](mailto:opencode@microsoft.com) にお問い合わせください。

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Mixed Reality デベロッパー センターの便利なリソース

| ![見つける](features/images/mrdevcenter/icon-discover.png) [見つける](https://docs.microsoft.com/windows/mixed-reality/)| ![設計](features/images/mrdevcenter/icon-design.png) [設計](https://docs.microsoft.com/windows/mixed-reality/design)| ![開発](features/images/mrdevcenter/icon-develop.png) [開発](https://docs.microsoft.com/windows/mixed-reality/development)| ![配布)](features/images/mrdevcenter/icon-distribute.png) [配布](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| HoloLens とイマーシブ ヘッドセット (VR) 向けの Mixed Reality エクスペリエンスを構築する方法を学習します。          | デザイン ガイドを入手します。 ユーザー インターフェイスを構築します。 対話式操作と入力について学習します。     | 開発ガイドを入手します。 テクノロジを学習します。 科学を理解します。       | 他のユーザー用にアプリを準備し、3D ランチャーの作成を検討します。 |

## <a name="useful-resources-on-azure"></a>Azure の便利なリソース

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/)| ![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![視覚サービス](features/images/mrdevcenter/icon-azurevisionservices.png) [視覚サービス](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Spatial Anchors は、時間が経過しても複数のデバイス間で位置が維持されるオブジェクトを使用した Mixed Reality エクスペリエンスを作成できる、クロスプラットフォーム サービスです。| 音声テキスト変換、話者認識、アプリケーションへの音声変換など Azure を利用した音声認識機能を検出、統合します。| コンピューター ビジョン、顔検出、感情認識、Video Indexer などのビジョン サービスを使用して画像またはビデオ コンテンツを特定、分析します。 |

## <a name="how-to-contribute"></a>貢献する方法

MRTK に投稿する方法については、「[投稿](contributing/contributing.md)」を参照してください。

## <a name="getting-help"></a>ヘルプの表示

MRTK に起因する問題が発生した場合、または何かを行う方法について質問がある場合は、いくつかのリソースが役に立ちます。

* バグ レポートを行う場合は、GitHub リポジトリで[イシューを報告](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)してください。
* ご質問がある場合は、[StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) か Slack の [mixed-reality-toolkit チャンネル](https://holodevelopers.slack.com/messages/C2H4HT858)のいずれかをご利用ください。 [自動招待センダー](https://holodevelopersslack.azurewebsites.net/)を使用して Slack コミュニティに参加することができます。
