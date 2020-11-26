---
title: Unreal での空間マッピング
description: Unreal で空間マッピングを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間マッピング, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: cd7e99230809c9d98f732e0dfa1f0b86d05c4365
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678811"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal での空間マッピング

## <a name="overview"></a>概要
空間マッピングを使用すると、HoloLens の周囲の世界を見せることで、物理的な世界の表面にオブジェクトを配置できるようになります。これにより、ホログラムがユーザーにとってより現実的に見えるようになります。 また、空間マッピングでは、実際の奥行きの手掛かりを利用して、ユーザーの世界にオブジェクトを固定します。これにより、これらのホログラムが実際に空間に存在することをユーザーに納得させることができます。空間に浮かんでいるホログラムやユーザーと一緒に動くホログラムは、それほどリアルではありません。 できるだけ快適さを追求してアイテムを配置したいと考えています。

空間マッピングの品質、配置、オクルージョン、レンダリングなどの詳細については、[空間マッピング](../../design/spatial-mapping.md) に関するドキュメントを参照してください。

## <a name="enabling-spatial-mapping"></a>空間マッピングの有効化

HoloLens で空間マッピングを有効にするには、次の手順を実行します。
- **[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまで下にスクロールします。    
    + **[HoloLens]** を選択し、 **[空間認知]** をオンにします。

HoloLens ゲームで空間マッピングをオプトインし、 **[MRMesh]** をデバッグするには、次のようにします。
1. **[ARSessionConfig]** を開き、 **[ARSettings] > [ワールド マッピング]** セクションを展開します。 

2. **[追跡対象ジオメトリからメッシュ データを生成する]** をオンにします。これにより、空間マッピング データの非同期取得を開始し、**MRMesh** を介して Unreal に表示するように HoloLens プラグインに指示されます。 
3. **MRMesh** ですべての三角形の白いワイヤーフレーム アウトラインを表示するには、 **[ワイヤーフレームでメッシュデータをレンダリングする]** をオンにします。 

![空間アンカー ストア準備完了](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>実行時の空間マッピング
次のパラメーターを変更して、空間マッピングのランタイム動作を更新できます。

- **[編集] > [プロジェクトの設定]** を開き、 **[プラットフォーム]** セクションまで下にスクロールして、 **[HoloLens] > [空間マッピング]** を選択します。 

![空間アンカーのプロジェクト設定](images/unreal-spatialmapping-projectsettings.PNG)

- **[Max Triangles Per Cubic Meter]\(立方メートルあたりの最大三角形数\)** で、空間マッピング メッシュの三角形の密度が更新されます。  
- **[Spatial Meshing Volume Size]\(空間メッシュのボリューム サイズ\)** は、空間マッピング データをレンダリングおよび更新するための、プレーヤー周りのキューブのサイズを示します。  
    + 予想されるアプリケーションの実行時環境が大きくなると思われる場合は、この値を現実世界のスペースに合わせて大きくしなければならない場合があります。  一方、アプリケーションでユーザーの周囲の表面にホログラムを配置するだけであれば、このフィールドを小さくすることができます。 ユーザーが移動するにつれて、空間マッピングのボリュームも移動します。 

## <a name="working-with-mrmesh"></a>MRMesh の操作
実行時に **MRMesh** にアクセスするには、次のようにします。
1. ブループリント アクターに **ARTrackableNotify** コンポーネントを追加します。 

![空間アンカーの AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** コンポーネントを選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。 
    - 監視するイベントの [ **+** ] ボタンをクリックします。 

![空間アンカーのイベント](images/unreal-spatialmapping-events.PNG)

この場合は、 **[追跡ジオメトリの追加]** イベントが監視され、空間マッピング データに一致する有効なワールド メッシュが検索されます。 イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。 

メッシュのマテリアルは、ブループリント イベント グラフまたは C++ で変更できます。 次のスクリーンショットは、ブループリントのルートを示しています。 

![空間アンカーの例](images/unreal-spatialmapping-example.PNG)

次のコードに示すように、C++ では、`OnTrackableAdded` デリゲートをサブスクライブして、使用可能になったらすぐに `ARTrackedGeometry` を取得することができます。 

> [!IMPORTANT]
> プロジェクトの build.cs ファイルでは、**PublicDependencyModuleNames** リストに **AugmentedReality** が含まれている **必要があります**。
> - これには **ARBlueprintLibrary.h** と **MRMeshComponent.h** が含まれます。これにより、**UARTrackedGeometry** の **MRMesh** コンポーネントを調べることができます。 

![空間アンカーの例の C++ コード](images/unreal-spatialmapping-examplecode.PNG)

空間マッピングは、**ARTrackedGeometries** によって表示される唯一のデータの種類ではありません。 `EARObjectClassification` が `World` であることを確認できます。これは、それが空間マッピング ジオメトリであることを意味します。 

更新および削除されたイベントでも、類似のデリゲートがあります。 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle` の順にクリックします。 

イベントの完全な一覧については、[UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API を参照してください。

## <a name="see-also"></a>関連項目
* [空間マッピング](../../design/spatial-mapping.md)
