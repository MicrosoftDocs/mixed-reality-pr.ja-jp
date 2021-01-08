---
title: MRTK のチュートリアル - 5. ソルバーを使用した動的なコンテンツの作成
description: このコースでは、Mixed Reality Toolkit (MRTK) のソルバーを使用して動的コンテンツを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, ソルバー
ms.localizationpriority: high
ms.openlocfilehash: 533aa1c9f2b0b7620e23d611714552fb19a5357b
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613506"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5.ソルバーを使用した動的なコンテンツの作成

## <a name="overview"></a>概要

このチュートリアルでは、複雑な空間配置シナリオを解決するために、MRTK で使用できる "ソルバー" という配置ツールを使用して、ホログラムを動的に配置する方法について学習します。 MRTK では、ソルバーとは、シーン内に存在する自分、ユーザー、他のゲーム オブジェクトをオブジェクトが追跡できるようにするために使用される、スクリプトと動作のシステムです。 これらは、特定の場所にスナップして、アプリをさらに直感的にするために使用することもできます。

## <a name="objectives"></a>目標

* MRTK ソルバーの紹介
* ソルバーを使用してユーザーをオブジェクトに誘導する方法を学習する
* ソルバーを使用してオブジェクトの位置を変更する方法を学習する

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所

 MRTK のソルバーは、MRTK SDK フォルダーにあります。 プロジェクトで使用可能なソルバーを表示するには、[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK]**  >  **[SDK]**  >  **[機能]**  >  **[ユーティリティ]**  >  **[ソルバー]** の順に移動します。

![Solvers フォルダーが選択されている Unity プロジェクト ウィンドウ](images/mr-learning-base/base-05-section1-step1-1.png)

このチュートリアルでは、Directional Indicator Solver と Tap To Place Solver の実装方法について説明します。 MRTK で利用可能なすべてのソルバーの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)に関するガイドを参照してください。

> [!NOTE]
> Directional Indicator Solver は、上記の [Solvers] フォルダーには含まれていません。これは試験的な機能であるため、[アセット] > [MRTK] > [SDK] > [試験的] > [機能] > [ユーティリティ] フォルダーにあります。

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Directional Indicator Solver を使用してユーザーをオブジェクトに誘導する

[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動し、 **[シェブロン]** プレハブをクリックして [階層] ウィンドウにドラッグします。次に、[変換] の **[位置]** を X = 0, Y = 0, Z = 2 に設定して、RoverExplorer オブジェクトの近くに配置します。

![新しく追加したシェブロン プレハブが選択されている Unity](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> シーンに含まれるカメラや他のアイコンがオブジェクトを見にくくしていたり操作の邪魔になったりしている場合は、上の図に示すように、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にできます。 ギズモ メニューと、それを使用してシーン ビューを最適化する方法の詳細については、Unity の <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">ギズモ メニュー</a>に関するドキュメントを参照してください。

新しく追加したシェブロン オブジェクトの名前を **Indicator** に変更し、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用して、**DirectionalIndicator** を追加します。

![DirectionalIndicator ソルバー コンポーネントが追加された Unity](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> ソルバーを追加する場合 (この例では DirectionalIndicator コンポーネント)、ソルバーで SolverHandler コンポーネントが必要になるため、それが自動的に追加されます。

> [!NOTE]
> Directional Indicator Controller (Script) は MRTK の一部ではありませんが、チュートリアル アセットには含まれていました。

DirectionalIndicator および SolverHandler コンポーネントを次のように構成します。

* **SolverHandler** コンポーネントの **[Tracked Target Type]\(追跡対象の種類\)** が **[ヘッド]** に設定されていることを確認します
* **RoverExplorer** を、[階層] ウィンドウから **[None (Transform)]\(なし (変換)\)** フィールドにドラッグして、**DirectionalIndicator** コンポーネントの **[Directional Target]\(方向のターゲット\)** に割り当てます
* **[View Offset]\(表示オフセット\)** を 0.2 に変更します

![DirectionalIndicator ソルバー コンポーネントが構成されている Unity](images/mr-learning-base/base-05-section2-step1-3.png)

[再生] ボタンを押してゲーム モードに入り、マウスの右ボタンを押したままにしてマウスを左右に動かし、視線入力の方向を回転させます。次の点に注意してください。

* RoverExplorer オブジェクトから視線を外すと、Indicator オブジェクトが表示され、RoverExplorer オブジェクトを指します

![DirectionalIndicator ソルバーが使用されている Unity 再生モードの分割ビュー](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> [シーン] ウィンドウにカメラの光線が表示されない場合は、上の図に示すように、ギズモ メニューが有効になっていることを確認してください。

> [!TIP]
> エディター内入力シミュレーションの使用方法については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)で「[エディター内ハンド入力シミュレーションを使用したシーンのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」ガイドを参照してください。

> [!TIP]
> コンピューターにマイクがある場合は、"toggle diagnostics"(診断をトグル) という音声コマンドを使用することにより、[ゲーム] ウィンドウに表示される診断パネルのアクティブ状態を簡単に切り替えることができます。 または、[MRTK Configuration Profile]\(MRTK 構成プロファイル\) > [診断] > [Enable Diagnostics System]\(診断システムを有効にする\) でも無効にできます。 ただし、開発中は、通常は診断システムをアクティブにしておくことをお勧めします。

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Tap to Place Solver を使用してオブジェクトの位置を変更する

[階層] ウィンドウで、RoverExplorer > **RoverAssembly** オブジェクトの順に選択します。次に、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用し、**Tap To Place (Script)** コンポーネントを追加して、次のように構成します。

* **SolverHandler** コンポーネントの **[Tracked Target Type]\(追跡対象の種類\)** が **[ヘッド]** に設定されていることを確認します
* **[Keep Orientation Vertical]\(向きを垂直に保つ\)** チェックボックスをオンにします
* **[Magnetic Surfaces]\(磁気サーフェス\)**  >  **[Element 0]\(要素 0\)** ドロップダウンから、 **[Spatial Awareness]\(空間認識\)**  以外のすべてのオプションをオフにします

![TapToPlace ソルバー コンポーネントが追加されて構成されている Unity](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> [Magnetic Surfaces]\(磁気サーフェス\) 設定により、オブジェクトを配置するときに Tap To Place (Script) コンポーネントで検出できるオブジェクトが決定します。 この設定を [Spatial Awareness]\(空間認識\) のみに変更することにより、Tap To Place (Script) コンポーネントは、[Spatial Awareness]\(空間認識\) という名前の Unity レイヤーのオブジェクトにのみ Rover を配置できるようになります。この Unity レイヤーは、既定で HoloLens によって生成される空間認識メッシュです。
>
>レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">レイヤー</a>に関するドキュメントを参照してください。

> [!TIP]
> Tap To Place 機能を HoloLens でテストするときにこの空間認識メッシュを表示したい場合は、空間メッシュ オブザーバーの表示オプションを一時的に [表示] に設定できます。 表示オプションを変更する方法については、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順を参照してください。

[階層] ウィンドウで RoverAssembly オブジェクトを選択したまま、[インスペクター] ウィンドウで **On Placing Started ()** イベントを見つけて、 **+** アイコンをクリックし、新しいイベントを追加します。

![TapToPlace OnPlacingStarted イベントが追加された Unity](images/mr-learning-base/base-05-section3-step1-2.png)

イベントを次のように構成します。

* **RoverAssembly** オブジェクトを、[階層] ウィンドウから **[None (Object)]\(なし (オブジェクト)\)** フィールドにドラッグして、On Placing Started () イベントのリスナーとして割り当てます
* **[関数なし]** ドロップダウンから、**TapToPlace** > **float SurfaceNormalOffset** の順に選択し、イベントがトリガーされたときの SurfaceNormalOffset プロパティ値を更新します
* 引数が **0** に設定されていることを確認します

![TapToPlace OnPlacingStarted イベントが構成された Unity](images/mr-learning-base/base-05-section3-step1-3.png)

[階層] ウィンドウの何もない場所を右クリックし、 **[3D オブジェクト]**  >  **[キューブ]** の順に選択して、地面を表す一時オブジェクトを作成し、**Transform** コンポーネントを次のように構成します。

* **位置**:X = 0、Y = -1.65、Z = 6
* **回転**:X = 0、Y = 0、Z = 0
* **スケール**:X = 10、Y = 0.2、Z = 10

![一時的な地面キューブ オブジェクトが追加されて配置された Unity](images/mr-learning-base/base-05-section3-step1-4.png)

[階層] ウィンドウで一時的な [キューブ] を選択したまま、[インスペクター] ウィンドウの **[レイヤー]** ドロップダウンを使用して、 **[Spatial Awareness]\(空間認識\)** レイヤーのみが含まれるようにキューブのレイヤー設定を変更します。

![一時的な地面キューブ オブジェクト レイヤーが空間認識に設定された Unity](images/mr-learning-base/base-05-section3-step1-5.png)

[再生] ボタンを押してゲーム モードに入り、マウスの右ボタンを押したまま、視線入力が RoverAssembly オブジェクトに当たるまでマウスを下方向に移動します。

![視線入力 RoverAssembly オブジェクトを含む Unity 再生モードの分割ビュー](images/mr-learning-base/base-05-section3-step1-6.png)

マウスの左ボタンをクリックして、Tap To Place プロセスを開始します。

![TapToPlace の配置が開始された Unity 再生モードの分割ビュー](images/mr-learning-base/base-05-section3-step1-7.png)

マウスの右ボタンを押したままにしてマウスを左右に動かし、視線入力の方向を回転させます。適切な位置に配置できたら、マウスの左ボタンをクリックします。

![TapToPlace の配置が終了した Unity 再生モードの分割ビュー](images/mr-learning-base/base-05-section3-step1-8.png)

ゲーム モードでの機能のテストが完了したら、キューブ オブジェクトを右クリックし、 **[削除]** を選択して、オブジェクトをシーンから削除します。

![一時的な地面キューブが選択されている Unity と [削除] コンテキスト ポップアップ メニュー](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK の Directional Indicator Solver を使用して、UI 要素でユーザーを直感的にオブジェクトに誘導する方法を学習しました。 Tap To Place Solver を使用してオブジェクトの位置を簡単に変更する方法についても学習しました。

MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)に関するガイドを参照してください。

[次のチュートリアル:6.ユーザー インターフェイスの作成](mr-learning-base-06.md)