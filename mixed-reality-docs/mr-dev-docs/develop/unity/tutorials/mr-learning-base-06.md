---
title: ユーザー インターフェイスの作成
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して静的および動的なユーザー インターフェイスを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, プレハブ, ホログラム, ヒント
ms.localizationpriority: high
ms.openlocfilehash: 4fe4b016be36e04abffeb415f690cc0c01a6f767
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635554"
---
# <a name="6-creating-user-interfaces"></a>6.ユーザー インターフェイスの作成

このチュートリアルでは、MRTK のボタンとメニュー プレハブを Unity の TextMeshPro コンポーネントと共に使用して、シンプルなユーザー インターフェイスを作成する方法について学習します。 また、ボタンでイベントがトリガーされるように構成する方法と、ユーザーに追加情報を提供する動的なヒント UI 要素を追加する方法についても学習します。

## <a name="objectives"></a>目標

* コレクション内のボタンを整理する方法を学習する
* MRTK のメニュー プレハブを使用する方法を学習する
* UI メニューとボタンを使用してホログラムを操作する方法を学習する
* テキスト要素を追加する方法を学習する
* オブジェクト上にヒントを動的に生成する方法を学習する

## <a name="creating-a-static-panel-of-buttons"></a>ボタンの静的パネルの作成

[階層] ウィンドウで、**RoverExplorer** オブジェクトを右クリックし、 **[Create Empty]\(空アイテムの作成\)** を選択して、RoverExplorer の子として空のオブジェクトを追加し、そのオブジェクトに **Buttons** と名前を付けて、**Transform** コンポーネントを次のように構成します。

* **位置**:X = -0.6、Y = 0.036、Z = -0.5
* **回転**:X = 90、Y = 0、Z = 0
* **スケール**:X = 1、Y = 1、Z = 1

![新しく作成された Buttons オブジェクトが選択され配置されている Unity](images/mr-learning-base/base-06-section1-step1-1.png)

[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動し、**PressableRoundButton** プレハブをクリックして **Buttons** オブジェクトにドラッグします。次に、PressableRoundButton を右クリックし、 **[複製]** を選択してコピーを作成します。この操作を、PressableRoundButton オブジェクトが全部で 3 個できるまで繰り返します。

![PressableRoundButton プレハブが新しく追加された Unity](images/mr-learning-base/base-06-section1-step1-2.png)

[階層] ウィンドウで、**Buttons** オブジェクトを選択します。次に、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用し、**GridObjectCollection** コンポーネントを追加して、次のように構成します。

* **並べ替えの種類**:子の順序
* **レイアウト**:横方向
* **セルの幅**:0.2
* **アンカー**:中央左

次に、 **[コレクションの更新]** ボタンをクリックして、Buttons オブジェクトの子オブジェクトの位置を更新します。

![GridObjectCollection コンポーネントが追加、構成、適用された Unity の Buttons オブジェクト](images/mr-learning-base/base-06-section1-step1-3.png)

[階層] ウィンドウで、それらのボタンに **Hints**、**Explode**、**Reset** という名前を付けます。

各ボタンについて、**SeeItSayItLabel** > **TextMeshPro** 子オブジェクトの順に選択し、[インスペクター] ウィンドウで、それぞれの **TextMeshPro - Text** コンポーネントのテキストをそのボタンの名前と一致するように変更します。

![ボタンのテキスト ラベルが構成された Unity](images/mr-learning-base/base-06-section1-step1-4.png)

完了したら、Buttons オブジェクトの子オブジェクトを折りたたみます。

[階層] ウィンドウで、**Hints** ボタン オブジェクトを選択します。次に、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。

* **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**PlacementHintsController** > **TogglePlacementHints ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![Hints ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Interactable コンポーネントは、すべてのオブジェクトを入力に対して簡単にインタラクティブかつレスポンシブにすることのできるオールインワン コンテナーです。 Interactable は、タッチ、ハンド レイ、音声などを含むすべての種類の入力のキャッチオールとして機能し、これらの対話をイベントと視覚的テーマの応答にファネルします。 さまざまな入力の種類に合わせて構成し、その視覚的テーマをカスタマイズする方法については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) ガイドを参照してください。

[階層] ウィンドウで、**Explode** ボタン オブジェクトを選択します。次に、[インスペクター] ウィンドウで、次のように **Interactable.OnClick ()** イベントを構成します。

* **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**ExplodedViewController** > **ToggleExplodedView ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![Explode ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-06-section1-step1-6.png)

[再生] ボタンを押してゲーム モードに入り、スペース バー ボタンを押したままにして手をアクティブにし、マウスを使用して **Hints** ボタンを押して、配置ヒント オブジェクトの可視性を切り替えます。

![[ヒント] ボタンが押されている Unity 再生モードの分割ビュー](images/mr-learning-base/base-06-section1-step1-7.png)

また、**Explode** ボタンを押して、分解ビューのオンとオフを切り替えます。

![[分解] ボタンが押されている Unity 再生モードの分割ビュー](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>ユーザーに追従する動的メニューの作成

[プロジェクト] ウィンドウで、 **[資産]**  >  **[MRTK]**  >  **[SDK]**  >  **[Features]\(機能\)**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[Menus]\(メニュー\)** フォルダーの順に移動し、 **[NearMenu4x1]** プレハブをクリックして [階層] ウィンドウにドラッグします。その [Transform]\(変換\) の **[Position]\(位置\)** を X = 0、Y = -0.4、Z = 0 に設定し、以下のように構成します。

* **SolverHandler** コンポーネントの **[Tracked Target Type]\(追跡対象の種類\)** が **[ヘッド]** に設定されていることを確認します
* **RadialView** Solver コンポーネントの横にあるチェックボックスをオンにして、既定で有効になるようにします

![新しく追加されたメニューの近くのプレハブが選択されている Unity](images/mr-learning-base/base-06-section2-step1-1.png)

[階層] ウィンドウで、オブジェクトの名前を **Menu** に変更し、**ButtonCollection** 子オブジェクトを展開して、次の 4 つのボタンを表示します。

![Menu オブジェクトが選択されて ButtonCollection オブジェクトが展開されている Unity](images/mr-learning-base/base-06-section2-step1-2.png)

ButtonCollection の最初のボタンの名前を Indicator に変更します。その後、[Inspector]\(インスペクター\) ウィンドウで、次のように Button Config Helper (Script) コンポーネントを構成します。

* ボタンの名前と一致するように **[Main Label Text]\(メイン ラベル テキスト\)** を変更します
* シェブロンのような見た目の Indicator オブジェクトを [None (Object)]\(なし (オブジェクト)\) フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**GameObject** > **SetActive (bool)** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します
* 引数チェックボックスが **オン** になっていることを確認します
* **アイコン** を [検索] アイコンに変更します

![Indicator ボタン オブジェクトのボタン構成ヘルパーが構成されている Unity](images/mr-learning-base/base-06-section2-step1-3.png)

シェブロン インジケーター オブジェクトを無効にするには、[Hierarchy]\(階層\) ウィンドウで、シェブロンのような見た目の Indicator オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで次のようにします。

* その名前の横にあるチェックボックスをオフにして、既定で非アクティブにします
* **[コンポーネントの追加]** ボタンを使用して **Directional Indicator Controller (Script)** コンポーネントを追加します

![Indicator オブジェクトが選択されて無効化され、DirectionalIndicatorController コンポーネントが追加された Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> これで、アプリの起動時にシェブロン インジケーターは既定で無効になり、[Indicator]\(インジケーター\) ボタンを押すと有効にできるようになりました。

2 番目のボタンの名前を **TapToPlace** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。

* ボタンの名前と一致するように **[Main Label Text]\(メイン ラベル テキスト\)** を変更します
* RoverExplorer > **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**TapToPlace** > **bool Enabled** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します
* **アイコン** を [hand with ray]\(手の光線を表示\) アイコンに変更します

![TapToPlace ボタン オブジェクトのボタン構成ヘルパーが構成されている Unity](images/mr-learning-base/base-06-section2-step1-5.png)

[階層] ウィンドウで **RoverAssembly** オブジェクトを選択してから、[インスペクター] ウィンドウで **Tap To Place (Script)** コンポーネントを次のように構成します。

* その名前の横にあるチェックボックスをオフにして、既定で非アクティブにします
* **On Placing Stopped ()** イベント セクションで、 **+** アイコンをクリックし、新しいイベントを追加します。
* RoverExplorer > **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**TapToPlace** > **bool Enabled** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オフ** になっていることを確認します

![TapToPlace コンポーネントが再構成された Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> これで、アプリの起動時に Tap to Place 機能は既定で無効になり、[Tap to Place] ボタンを押すと有効にできるようになりました。 また、Tap to Place が完了すると、自動的に機能は無効になります。

## <a name="adding-text-to-the-scene"></a>シーンへのテキストの追加

[階層] ウィンドウで、**Table** オブジェクトを右クリックし、 **[3D オブジェクト]**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** の順に選択して、テキスト オブジェクトを Table オブジェクトの子として追加します。次に、[インスペクター] ウィンドウで、次のように **Rect Transform** コンポーネントを構成します。

* **[Pos Y]\(位置 Y\)** を 1 に変更します
* **[幅]** を 1 に変更します
* **[高さ]** を 1 に変更します
* **[回転 X]** を 90 に変更します

![新しく作成された TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-base/base-06-section3-step1-1.png)

次に、**TextMeshPro - Text** コンポーネントを次のように構成します。

* **[テキスト]** を Rover Explorer に変更します
* **[フォント スタイル]** を [太字] に変更します
* **[フォント サイズ]** を 1 に変更します
* [追加設定] > **[余白]** を 0.03 に変更します

![TextMeshPro コンポーネントが構成された Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>ヒントの追加

[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK]**  >  **[SDK]**  >  **[機能]**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[ヒント]** フォルダーの順に移動して、ヒント プレハブを見つけます。

![ToolTips フォルダーが選択されている Unity プロジェクト ウィンドウ](images/mr-learning-base/base-06-section4-step1-1.png)

[階層] ウィンドウで、RoverExplorer > **RoverParts** オブジェクトの順に展開し、そのすべての子のローバー パーツ オブジェクトを選択します。次に、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用し、**ToolTipSpawner** コンポーネントを追加して、次のように構成します。

* ヒントを表示するにはユーザーがそのパーツに視線を向けることが必要であるようにするため、 **[Focus Enabled]\(フォーカスが有効\)** チェックボックスがオンになっていることを確認します
* **Simple Line ToolTip** プレハブを、[プロジェクト] ウィンドウから **[Prefab]\(プレハブ\)** フィールドに割り当てます
* [ToolTip Override Settings]\(ヒントのオーバーライド設定\) > **[設定モード]** を **[オーバーライド]** に変更します
* [ToolTip Override Settings]\(ヒントのオーバーライド設定\) > **[Manual Pivot Local Position Y]\(手動のピボットのローカル位置 Y\)** を **1.5** に変更します

![すべての探査車パーツ オブジェクトが選択され、ToolTipSpawner コンポーネントが追加されて構成された Unity](images/mr-learning-base/base-06-section4-step1-2.png)

[階層] ウィンドウで、最初のローバー パーツを RoverParts > **Camera_Part** の順で選択し、**ToolTipSpawner** コンポーネントを次のように構成します。

* パーツの名前を反映するように、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Camera** に変更します

![カメラの ToolTipText が構成された Unity](images/mr-learning-base/base-06-section4-step1-3.png)

それぞれのローバー パーツ オブジェクトに対してこの手順を **繰り返し** て、**ToolTipSpawner** コンポーネントを次のように構成します。

* **Generator_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Generator** に変更する
* **Lights_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Lights** に変更する
* **UHFAntenna_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **UHF Antenna field** に変更する
* **Spectrometer_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Spectrometer** に変更する

[再生] ボタンを押してゲーム モードに入り、マウスの右ボタンを押したまま、視線入力がパーツの 1 つに当たるまでマウスを移動します。すると、そのパーツのヒントが次のように表示されます。

![視線によってツールヒントがトリガーされた Unity の再生モード分割ビュー](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK で用意されているボタンとメニュー プレハブを Unity の TextMeshPro コンポーネントと共に使用して、シンプルなユーザー インターフェイスを作成する方法について学習しました。また、ボタンが押されたときにイベントがトリガーされるようにボタンを構成する方法についても学習しました。 さらに、動的なヒント UI 要素を追加して、ユーザーに追加情報を提供する方法についても学習しました。

> [!div class="nextstepaction"]
>[次のチュートリアル:7.3D オブジェクトの操作](mr-learning-base-07.md)
