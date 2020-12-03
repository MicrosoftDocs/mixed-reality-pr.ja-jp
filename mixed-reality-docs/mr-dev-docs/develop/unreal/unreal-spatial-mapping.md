---
title: Unreal での空間マッピング
description: Unreal で空間マッピングを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間マッピング, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354382"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal での空間マッピング

空間マッピングを使用すると、HoloLens の周囲の世界を見せることで、物理的な世界の表面にオブジェクトを配置できるようになります。これにより、ホログラムがユーザーにとってより現実的に見えるようになります。 また、空間マッピングでは、実際の奥行きの手掛かりを利用して、ユーザーの世界にオブジェクトを固定します。これにより、これらのホログラムが実際に空間に存在することをユーザーに納得させることができます。空間に浮かんでいるホログラムやユーザーと一緒に動くホログラムは、それほどリアルではありません。 できるだけ快適さを追求してアイテムを配置したいと考えています。

空間マッピングの品質、配置、オクルージョン、レンダリングなどの詳細については、[空間マッピング](../../design/spatial-mapping.md) に関するドキュメントを参照してください。

## <a name="enabling-spatial-mapping"></a>空間マッピングの有効化

HoloLens で空間マッピングを有効にするには、次の手順を実行します。
- **[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまで下にスクロールします。    
    + **[HoloLens]** を選択し、 **[空間認知]** をオンにします。

![空間認知が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-spatial-mapping-img-01.png)

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

最初に、空間マッピングを開始する必要があります。

![空間マッピング キャプチャの種類が強調表示されている ToggleARCapture 関数のブループリント](images/unreal-spatial-mapping-img-02.png)

空間の空間マッピングのキャプチャが済んだら、空間マッピングをオフにすることをお勧めします。  空間マッピングは、一定の時間が経過した後、または各方向のレイキャストから MRMesh に対する衝突が返されるようになったら、完了できます。

実行時に **MRMesh** にアクセスするには、次のようにします。
1. ブループリント アクターに **ARTrackableNotify** コンポーネントを追加します。 

![空間アンカーの AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** コンポーネントを選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。 
    - 監視するイベントの [ **+** ] ボタンをクリックします。 

![空間アンカーのイベント](images/unreal-spatialmapping-events.PNG)

この場合は、 **[追跡ジオメトリの追加]** イベントが監視され、空間マッピング データに一致する有効なワールド メッシュが検索されます。 イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。 

メッシュのマテリアルは、ブループリント イベント グラフまたは C++ で変更できます。 次のスクリーンショットは、ブループリントのルートを示しています。 

![空間アンカーの例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>C++ での空間マッピング

ゲームの build.cs ファイルで、**AugmentedReality** と **MRMesh** を PublicDependencyModuleNames リストに追加します。

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

MRMesh にアクセスするには、**OnTrackableAdded** デリゲートをサブスクライブします。

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> 更新および削除イベントにも、それぞれ **AddOnTrackableUpdatedDelegate_Handle** および **AddOnTrackableRemovedDelegate_Handle** という同様のデリゲートがあります。
>
> イベントの完全な一覧については、[UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API を参照してください。

## <a name="see-also"></a>関連項目
* [空間マッピング](../../design/spatial-mapping.md)
