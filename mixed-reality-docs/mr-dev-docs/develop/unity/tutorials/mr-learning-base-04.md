---
title: MRTK のチュートリアル - 4. シーンへのオブジェクトの配置
description: このコースでは、シーンにオブジェクトを配置する方法と、Mixed Reality Toolkit (MRTK) を使用してグリッド内のオブジェクトを整理する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, ソルバー, Grid Object Collection
ms.localizationpriority: high
ms.openlocfilehash: 27964cad03111a3f7dad89c66df0cb9a4f95a9e2
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579211"
---
# <a name="4-positioning-objects-in-the-scene"></a>4.シーンへのオブジェクトの配置

## <a name="overview"></a>概要

このチュートリアルでは、チュートリアルのアセットをインポートし、シーンに指定されたオブジェクトを配置します。

## <a name="objectives"></a>目標

* シーンにオブジェクトを配置する方法について学ぶ
* MRTK の Grid Object Collection 機能の使用方法について学ぶ

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

次の Unity カスタム パッケージをダウンロードしてインポートします。

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、[MRTK のインポート](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)に関する説明を参照してください。

## <a name="creating-the-parent-object"></a>親オブジェクトの作成

[Hierarchy]\(階層\) ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空アイテムの作成\)** を選択してシーンに空のオブジェクトを追加します。

![Unity の [Create Empty]\(空アイテムの作成\) コンテキスト ポップアップ メニュー](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> 上の図のようにシーンとゲーム ウィンドウを並べて表示するには、ゲーム ウィンドウをシーン ウィンドウの右側にドラッグします。 ワークスペースのカスタマイズの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。

新規作成したオブジェクトを右クリックし、 **[Rename]\(名前の変更\)** を選択して、名前を **[RoverExplorer]** に変更します。

![Unity の [Rename]\(名前の変更\) コンテキスト ポップアップ メニュー](images/mr-learning-base/base-04-section2-step1-2.png)

[RoverExplorer] オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。

* **位置**:X = 0、Y = -0.6、Z = 2
* **回転**:X = 0、Y = 0、Z = 0
* **スケール**:X = 1、Y = 1、Z = 1

![RoverExplorer オブジェクトが選択され配置されている Unity](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> カメラはユーザーのヘッドを示し、X = 0、Y = 0、Z = 0 の基点に配置されています。 一般に、Unity の 1 単位は現実世界の約 1 m に相当します。 ただし、これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。 上のシナリオで RoverExplorer は、ユーザーのヘッドの 2 m 前、0.6 m 下に配置されています。

## <a name="adding-the-tutorial-prefabs"></a>チュートリアル プレハブの追加

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。

![[Prefabs]\(プレハブ\) フォルダーが選択されているプロジェクト ウィンドウが表示された Unity](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">プレハブ</a>は、Unity アセットとして格納されている事前構成済みの GameObject であり、プロジェクト全体で再利用できます。

[Project]\(プロジェクト\) ウィンドウで **[テーブル]** プレハブを **[RoverExplorer]** オブジェクトにクリックしてドラッグし、[RoverExplorer] オブジェクトの子にします。次いで [Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。

* **位置**:X = 0、Y = -0.005、Z = 0
* **回転**:X = 0、Y = 0、Z = 0
* **スケール**:X = 1.2、Y = 0.01、Z = 1.2

![新しく追加された Table プレハブが選択され配置されている Unity](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> 次の図のようにシーンを表示するには、[Scene]\(シーン\) ウィンドウの右上隅にある <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">[Scene Gizmo]</a>\(シーン ギズモ\) を使用して、前の Z 軸に沿うように表示角度を調整します。[MixedRealityPlayspace] オブジェクトをダブルクリックし、カメラにフォーカスを当て、必要に応じて拡大します。

[Project]\(プロジェクト\) ウィンドウで **[RoverAssembly]** プレハブを **[RoverExplorer]** オブジェクトにクリックしてドラッグし、[RoverExplorer] オブジェクトの子にします。次いで [Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。

* **位置**:X = -0.1、Y = 0、Z = 0
* **回転**:X = 0、Y = -135、Z = 0
* **スケール**:X = 1、Y = 1、Z = 1

![新しく追加された RoverAssembly プレハブが選択され配置されている Unity](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>コレクション内のオブジェクトの整理

[Hierarchy]\(階層\) ウィンドウで、 **[RoverExplorer]** オブジェクトを右クリックし、RoverExplorer の子として空のオブジェクトを追加するために **[Create Empty]\(空アイテムの作成\)** を選択します。そのオブジェクトには、 **[RoverParts]** と名前を付け、次のように **[Transform]\(変換\)** コンポーネントを構成します。

* **位置**:X = 0、Y = 0.06、Z = 0
* **回転**:X = 0、Y = 90、Z = 0
* **スケール**:X = 1、Y = 1、Z = 1

![新しく作成された RoverParts オブジェクトが選択され配置されている Unity](images/mr-learning-base/base-04-section4-step1-1.png)

[Hierarchy]\(階層\) ウィンドウで、[RoverExplorer]、[RoverAssembly]、[RoverModel]、 **[Parts]\(パーツ\)** の子オブジェクトをすべて選択し、それらを右クリックして、 **[Duplicate]\(重複\)** を選択し、各パーツのコピーを作成します。

![すべてのパーツが選択され、[Duplicate]\(重複\) コンテキスト ポップアップ メニューが表示されている Unity](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> 隣接するオブジェクトを複数選択するには、SHIFT キーを押しながら、マウスを使用して最初と最後のオブジェクトを選択します。

新しく複製した [Parts]\(パーツ\) 子オブジェクトを選択した状態で、それらをクリックして **[RoverParts]** オブジェクトにドラッグし、それらを RoverParts オブジェクトの子オブジェクトにします。

![RoverParts オブジェクトの子として新しく複製されたパーツが表示されている Unity](images/mr-learning-base/base-04-section4-step1-3.png)

ご自分のシーンで簡単に操作するには、[階層] ウィンドウでオブジェクトの左側にある **目** のアイコンをクリックして、 **[RoverAssembly]** オブジェクトの **シーンの可視性** をオフに設定します。 これにより、ゲーム内での可視性は変えずに、[Scene]\(シーン\) ウィンドウ内でオブジェクトを非表示にできます。

![RoverAssembly シーンの可視性がオフにされた Unity](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> シーンの可視性の制御と、それらを使用したシーン ビューとワークフローの最適化方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。

[Hierarchy]\(階層\) ウィンドウで、RoverParts の子オブジェクトの名前に追加された **(1)** を **_Part** に置き換え、整理します。

![重複するパーツ名が整理された Unity](images/mr-learning-base/base-04-section4-step1-5.png)

[Hierarchy]\(階層\) ウィンドウで **[RoverParts]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンをクリックします。次に、 **[GridObjectCollection]** を検索して選択し、RoverParts オブジェクトに GridObjectCollection コンポーネントを追加します。

![RoverParts オブジェクトへの Grid Object Collection のコンポーネントの追加が進行中の Unity](images/mr-learning-base/base-04-section4-step1-6.png)

**GridObjectCollection** コンポーネントの値を次のように構成します。

* **並べ替えの種類**:アルファベット
* **レイアウト**:横方向
* **セルの幅**:0.25
* **Distance from parent (親からの距離)** :0.38

![GridObjectCollection コンポーネントが構成された Unity](images/mr-learning-base/base-04-section4-step1-7.png)

次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、次のように RoverParts の子オブジェクトの位置を更新します。

![GridObjectCollection コンポーネントが適用された Unity](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、シーン内のオブジェクトをユーザーに対して配置し、MRTK の Grid Object Collection 機能を使用してコレクション内のオブジェクトを整理する方法について学習しました。

> [!div class="nextstepaction"]
>[次のチュートリアル:5.ソルバーを使用した動的なコンテンツの作成](mr-learning-base-05.md)
