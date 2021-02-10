---
title: 3D オブジェクトの操作
description: このコースでは、Mixed Reality ツールキット (MRTK) を使用して、Mixed Reality アプリで 3D オブジェクトと対話して操作する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality ツールキット, UWP, オブジェクトの操作, 境界コントロール
ms.localizationpriority: high
ms.openlocfilehash: f92eca294e2114207a5e28ebe80aa480b9029b66
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590448"
---
# <a name="7-interacting-with-3d-objects"></a>7.3D オブジェクトの操作

このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にし、許可される操作の種類を制限する方法について学習します。 また、オブジェクトの操作をより簡単に制御できるように、3D オブジェクトの周囲に境界コントロールを追加する方法について学習します。

## <a name="objectives"></a>目標

* 3D オブジェクトを操作できるように構成する方法について学習する
* 3D オブジェクトに境界コントロールを追加する方法について学習する

## <a name="manipulating-3d-objects"></a>3D オブジェクトの操作

このセクションでは、「[シーン内のオブジェクトの配置](mr-learning-base-04.md)」チュートリアルで、テーブルで構成したすべての探査車 (Rover) のパーツを操作する機能を追加します。

これを実現するための主な手順は次のとおりです。

1. すべてのパーツ オブジェクトに Object Manipulator (Script) コンポーネントを追加する
2. すべてのパーツ オブジェクトに NearInteractionGrabbable コンポーネントを追加する
3. Object Manipulator (Script) コンポーネントを構成する

> [!NOTE]
> **オブジェクトを操作** できるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、たとえばボックス コライダー
> * **Object Manipulator (Script)** コンポーネント
>
> オブジェクトを **操作** し、**追跡対象の手でオブジェクトをつかむ** ことができるようにするには、オブジェクトに次のコンポーネントが必要です。
>
> * **Collider** コンポーネント、たとえばボックス コライダー
> * **Object Manipulator (Script)** コンポーネント
> * **NearInteractionGrabbable** コンポーネント

さらに、探査車のパーツを Rover に配置して完全な探査車アセンブリにすることができるように、Rover Explorer を構成します。

[階層] ウィンドウで、RoverExplorer > **RoverParts** オブジェクトの順に展開し、そのすべての子の探査車のパーツ オブジェクトと **RoverAssembly** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、選択されたすべてのオブジェクトに次のコンポーネントを追加します。

* **Object Manipulator (Script)** コンポーネント
* **NearInteractionGrabbable** コンポーネント
* **Part Assembly Controller (Script)** コンポーネント

![RoverAssembly とすべての探査車パーツ オブジェクトが選択され、コンポーネントが追加されている Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> 互いに隣接していない複数のオブジェクトを選択するには、CTRL キーを押しながらマウスを使用して、任意のオブジェクトを選択します。

> [!NOTE]
> Object Manipulator (Script) を追加すると、この場合、Object Manipulator (Script) は Constraint Manager (Script) に依存しているため、それが自動的に追加されます。

> [!NOTE]
> このチュートリアルでは、コライダーが既に探査車のパーツに追加されています。 コライダーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">コライダー</a>に関するドキュメントを参照してください。

> [!NOTE]
> Part Assembly Controller (Script) は MRTK の一部ではありませんが、チュートリアル アセットには含まれていました。

すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトを引き続き選択した状態で、[インスペクター] ウィンドウで、次のように **Object Manipulator (Script)** コンポーネントを構成します。

* **[両手を使った操作の種類]** ドロップダウンで、[スケール] をオフにし、 **[移動]** と **[回転]** のみが有効になるようにします

![[Two Handed Manipulation Type]\(両手を使った操作の種類\) が構成された Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> この時点で、すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトのオブジェクト操作が有効になりました。

[プロジェクト] ウィンドウで、 **[パッケージ]**  >  **[Mixed Reality Toolkit Standard Assetss]**  >  **[Audio]** フォルダーに移動して、オーディオ クリップを見つけます。

![[Audio] フォルダーが選択されているプロジェクト ウィンドウが表示された Unity](images/mr-learning-base/base-07-section1-step1-3.png)

[階層] ウィンドウで、すべての **探査車のパーツ オブジェクト** をもう一度選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用し、**Audio Sources** コンポーネントを追加して、次のように構成します。

* **MRTK_Scale_Start** オーディオ クリップを **AudioClip** フィールドに割り当てます
* **[Play On Awake]\(起動時に再生\)** チェックボックスをオフにします
* **[Spatial Blend]\(空間ブレンド\)** を 1 に変更します

![すべての探査車パーツ オブジェクトが選択され、Audio Source コンポーネントが追加され構成されている Unity](images/mr-learning-base/base-07-section1-step1-4.png)

[階層] ウィンドウで、RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** オブジェクトの順に展開し、すべての配置ヒント オブジェクトを表示します。その後、最初の探査車のパーツである、RoverParts > **Camera_Part** の順に選択し、**Part Assembly Controller (Script)** コンポーネントを次のように構成します。

* **Camera_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます

![Camera_Part PartAssemblyController コンポーネントが構成された Unity](images/mr-learning-base/base-07-section1-step1-5.png)

残りの探査車のパーツ オブジェクトと RoverAssembly オブジェクトのそれぞれに対して、この手順を **繰り返し**、次のように **Part Assembly Controller (Script)** コンポーネントを構成します。

* **Generator_Part** については、**Generator_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます
* **Lights_Part** については、**Lights_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます
* **UHFAntenna_Part** については、**UHFAntenna_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます
* **Spectrometer_Part** については、**Spectrometer_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます
* **RoverAssembly** については、オブジェクト自体 (つまり、同じ **RoverAssembly** オブジェクト) を **[Location To Place]\(配置する場所\)** フィールドに割り当てます

[階層] ウィンドウで、[RoverExplorer] > [ボタン] > **[リセット]** ボタン オブジェクトの順に選択します。その後、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。

* **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、**PartAssemblyController** > **ResetPlacement ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します

![[リセット] ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-07-section1-step1-6.png)

ゲーム モードになったら、近距離または遠距離操作を使用して、探査車のパーツを Rover に配置できます。 パーツは、対応する配置ヒントに近づくと、自動的に所定の位置にはめ込まれ、Rover の一部になります。 配置をリセットする場合は、[リセット] ボタンを押すことができます。

![[リセット] ボタンが押されている再生モードの分割ビューが表示された Unity](images/mr-learning-base/base-07-section1-step1-7.png)

Object Manipulator コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[オブジェクト マニピュレーター](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)」のガイドを参照してください。

## <a name="adding-bounds-control"></a>境界コントロールの追加

境界コントロールを使用すると、拡大縮小および回転に使用できるハンドルが提供され、近距離と遠距離操作の両方のオブジェクト操作が片手で直感的にしやすくなります。

この例では、BoundsControl を RoverExplorer オブジェクトに追加して、エクスペリエンス全体を簡単に移動、回転、および拡大縮小できるようにします。 また、境界コントロールのオンとオフを切り替えられるように、メニューを構成します。

[階層] ウィンドウで、 **[RoverExplorer]** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、以下のコンポーネントを追加します。

* **BoundsControl** コンポーネント
* **Object Manipulator (Script)** コンポーネント

その後、すべてのコンポーネントの横にあるチェックボックスを **オフ** にして、既定で **無効** になるようにします。

![RoverExplorer オブジェクトが選択され、コンポーネントが追加され無効にされている Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> 境界コントロールの視覚エフェクトは実行時に作成されるため、ゲーム モードに入る前には表示されません。

> [!NOTE]
>実行時に、BoundsControl コンポーネントによって NearInteractionGrabbable コンポーネントが自動的に追加されます。 したがって、このコンポーネントを追加して、追跡対象の手で囲まれたオブジェクトをつかむ必要はありません。

> [!NOTE]
>Object Manipulator (Script) により、Constraint Manager (Script) が自動的に追加されます

[階層] ウィンドウで、[メニュー] > **[ButtonCollection]** オブジェクトの順に展開して 4 つのボタンを表示し、3 番目のボタンの名前を **BoundsControl_Enable** に変更します。その後、[インスペクター] ウィンドウで、**Button Config Helper (Script)** コンポーネントを次のように構成します。

* **[Main Label Text]\(メイン ラベル テキスト\)** を **[有効]** に変更します
* **RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[BoundsControl]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します
* 小さい **[+]** アイコンをクリックして、別のイベントを追加します
* **RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します
* **[Icon]\(アイコン\)** は、"境界コントロールがあるキューブ" アイコンのままにしておきます

![BoundsControl_Enable ボタン オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-2.png)

4 番目と最後のボタンの名前を **BoundsControl_Disable** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。

* **[Main Label Text]\(メイン ラベル テキスト\)** を **[無効]** に変更します
* **RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[BoundsControl]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オフ** になっていることを確認します
* 小さい **[+]** アイコンをクリックして、別のイベントを追加します
* **RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オフ** になっていることを確認します
* **[Icon]\(アイコン\)** を、"境界コントロールがあるキューブ" アイコンに変更します

![BoundsControl_Disable ボタン オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-3.png)

ゲーム モードに入り、[Enable]\(有効\) ボタンをクリックして境界コントロールを有効にしたら、近距離または遠距離操作を使用して、境界コントロールの移動、回転、および拡大縮小を行い、[Disable]\(無効\) ボタンを使用して、境界コントロールをもう一度無効にすることができます。

![境界コントロールが操作されている Unity Play モードの分割ビュー](images/mr-learning-base/base-07-section2-step1-4.png)

Bounds Control コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界コントロール](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)に関するガイドを参照してください。

## <a name="congratulations"></a>結論

このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にする方法と、許可される操作の種類を制限する方法について学習しました。 また、3D オブジェクトの周囲に境界コントロールを追加して、オブジェクトの操作をより簡単に制御できるようにする方法についても学習しました。

> [!div class="nextstepaction"]
> [次のチュートリアル:8.視線追跡の使用](mr-learning-base-08.md)
