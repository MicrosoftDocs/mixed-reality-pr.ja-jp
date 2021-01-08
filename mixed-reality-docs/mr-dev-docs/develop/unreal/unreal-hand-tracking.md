---
title: Unreal での手の追跡
description: Unreal mixed reality アプリで、入力、ポーズ、ハンドメッシュ、ライブリンクアニメーションをハンドトラッキングする方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手動追跡、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010162"
---
# <a name="hand-tracking-in-unreal"></a>Unreal での手の追跡

ハンドトラッキングシステムは、ユーザーのてのひらとフィンガーを入力として使用します。 各指の位置と回転に関するデータ、palm 全体、およびハンドジェスチャを使用できます。 Unreal 4.26 以降、ハンドトラッキングは Unreal HeadMountedDisplay プラグインに基づいており、すべての XR プラットフォームとデバイスで共通の API を使用します。 Windows Mixed Reality と OpenXR システムの機能は同じです。

## <a name="hand-pose"></a>手の形

手の形では、ユーザーの手と指を入力として追跡し、使用することができます。これは、ブループリントと C++ の両方でアクセスできます。 Unreal API は、Unreal エンジンとの間で同期されたティックを使用して、データを座標系として送信します。

![手スケルトン](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>ハンドライブリンクアニメーション

[Live Link プラグイン](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)を使用して、手の形でアニメーションに公開されます。

Windows Mixed Reality とライブリンクプラグインが有効になっている場合:
1. [ **ウィンドウ > ライブリンク** ] を選択して、ライブリンクエディターウィンドウを開きます。
2. **ソース** を選択し、 **Windows Mixed Reality の追跡ソース** を有効にする

![ライブリンクのソース](images/unreal/live-link-source.png)

ソースを有効にし、アニメーション資産を開いた後、[**プレビューシーン**] タブの [**アニメーション**] セクションを展開すると、追加のオプションが表示されません。

![ライブリンクアニメーション](images/unreal/live-link-animation.png)

ハンドアニメーション階層は、の場合と同じ `EWMRHandKeypoint` です。 アニメーションは、 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** を使用して再ターゲットできます。

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)

また、エディターでサブクラス化することもできます。

![ライブリンクの再マップ](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>手動メッシュ

### <a name="hand-mesh-as-a-tracked-geometry"></a>追跡ジオメトリとしてのハンドメッシュ

> [!IMPORTANT]
> OpenXR の追跡されたジオメトリとして手メッシュを取得するには、[**有効な追跡ジオメトリ** での **ハンドメッシュを使用** する。

このモードを有効にするには **、次のように****設定** する必要があります。

![イベント開始再生のブループリントを設定して、有効な追跡ジオメトリモードでハンドメッシュ関数を使用する](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> 両方のモードを同時に有効にすることはできません。 1つを有効にした場合、もう一方は自動的に無効になります。

### <a name="accessing-hand-mesh-data"></a>手メッシュデータへのアクセス

![手動メッシュ](images/unreal/hand-mesh.png)

手作業のメッシュデータにアクセスするには、次のことを行う必要があります。
- **Arsessionconfig** 資産を選択し、 **AR の設定-> 世界のマッピング** 設定を展開して、[追跡された **ジオメトリからメッシュデータを生成** する] チェックボックスをオンにします。

既定のメッシュパラメーターを次に示します。

1.  遮蔽にメッシュデータを使用する
2.  メッシュデータの競合を生成する
3.  メッシュデータの Nav メッシュを生成します
4.  ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター

これらのパラメーター値は、空間マッピングメッシュと手動メッシュの既定値として使用されます。 これらは、任意のメッシュのブループリントまたはコードでいつでも変更できます。

### <a name="c-api-reference"></a>C++ API リファレンス
`EEARObjectClassification`を使用すると、すべての追跡可能なオブジェクトで手動メッシュ値を検索できます。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

システムによって追跡可能なオブジェクト (手メッシュを含む) が検出されると、次のデリゲートが呼び出されます。

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

デリゲートハンドラーが以下の関数シグネチャに従うことを確認します。

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

メッシュデータには、を使用してアクセスでき  `UARTrackedGeometry::GetUnderlyingMesh` ます。

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>ブループリント API リファレンス

ブループリントを使用するには、次のようにします。
1. **ARTrackableNotify** コンポーネントをブループリントアクターに追加する

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. [ **詳細** ] パネルにアクセスし、[ **イベント** ] セクションを展開します。

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. イベントグラフ内の次のノードを使用して、追跡したジオメトリの追加/更新/削除を上書きします。

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>OpenXR での手メッシュの視覚化

手動メッシュを視覚化するには、エピックの XRVisualization プラグインを [Microsoft OpenXR プラグイン](https://github.com/microsoft/Microsoft-OpenXR-Unreal)と共に使用することをお勧めします。 

次に、ブループリントエディターで、次のように、**有効な XRVisualization** をパラメーターとして使用して、 [Microsoft OpenXR Plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal)の **Set use ハンドメッシュ** 関数を使用する必要があります。

![イベント開始再生のブループリントを設定して、有効な xrvisualization モードでハンドメッシュ関数を使用する](images/unreal-hand-tracking-img-05.png)

レンダリングプロセスを管理するには、XRVisualization から **レンダーモーションコントローラー** を使用する必要があります。

![レンダーモーションコントローラー関数に接続された、motion controller データ関数のブループリント](images/unreal-hand-tracking-img-06.png)

結果は次のようになります。

![人間の手で店舗たデジタルハンドの画像](images/unreal-hand-tracking-img-07.png) 

カスタムシェーダーを使用したハンドメッシュの描画など、さらに複雑なものが必要な場合は、メッシュを追跡対象のジオメトリとして取得する必要があります。 

## <a name="hand-rays"></a>手の光線

オブジェクトを取得したり、ボタンを押したりするなど、密接な相互作用を手にすることができます。 ただし、場合によっては、ユーザーから離れた場所にあるホログラムを使用する必要があります。 これは、C++ とブループリントの両方でポインティングデバイスとして使用できる手書き線で実現できます。 離れた場所から遠くに伸びる光線を描画することができます。また、Unreal 射線 tracing の助けを得て、それ以外の場合には外れているホログラムを選択します。 

> [!IMPORTANT]
> すべての関数の結果はすべてのフレームに変更されるため、すべてが呼び出し可能になります。 純粋関数と純粋でない関数、または呼び出し可能関数の詳細については、「 [関数](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)のブループリントユーザー guid」を参照してください。

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>ジェスチャ

HoloLens 2 は、空間ジェスチャを追跡します。これは、これらのジェスチャを入力としてキャプチャできることを意味します。 ジェスチャの追跡は、サブスクリプションモデルに基づいています。 追跡するジェスチャをデバイスに通知するには、"ジェスチャの構成" 機能を使用する必要があります。 ジェスチャの詳細については、「 [HoloLens 2 の基本的な使用方法](https://docs.microsoft.com/hololens/hololens2-basic-usage) 」を参照してください。

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [ローカル空間アンカー](unreal-spatial-anchors.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。
