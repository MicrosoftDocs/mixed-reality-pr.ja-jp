---
title: Unreal のマテリアルに関する推奨事項
description: Unreal engine のマテリアルの概要。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開発、マテリアル、ドキュメント、ガイド、特徴、ホログラム、ゲーム開発
ms.openlocfilehash: bfce6e6bf8acd58821dba1213e1f1ab571d85a0c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684546"
---
# <a name="material-recommendations-in-unreal"></a>Unreal のマテリアルに関する推奨事項

Unreal Engine では、マテリアルはパフォーマンスを向上させることができます。 このページは、最高のパフォーマンスを得るために使用する必要がある基本設定のクイックスタートとして機能します。

## <a name="using-customizeduvs"></a>CustomizedUVs の使用

素材に UVs のタイルを提供する必要がある場合は、テクスチャノードの UV を直接変更するのではなく、CustomizedUVs を使用する必要があります。 CustomizedUVs は、ピクセルシェーダーではなく頂点シェーダーで UV 操作を実行できるようにします。 

![Unreal のマテリアル設定](images/unreal-materials-img-01c.png)

素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) と、次のスクリーンショットのベストプラクティスの例を参照してください。

推奨される[ ![ 未 ](images/unreal-materials-img-01.png) 設定の資料での推奨資料の設定](images/unreal-materials-img-01.png#lightbox) 
 *Recommended material setup*

推奨される[ ![ unreal ](images/unreal-materials-img-01b.png) 以外のマテリアルのセットアップでの推奨されるマテリアル以外の設定](images/unreal-materials-img-01b.png#lightbox) 
 *Non-recommended material setup*

## <a name="changing-blend-mode"></a>Blend モードの変更

特に複雑な理由がない限り、blend モードを不透明に設定する必要があります。 マスクされた半透明な素材は低速です。 素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。

![Blend モードの変更](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>モバイルのライティングを更新しています

完全有効桁数はオフにする必要があります。 ライトマップライトは、方向情報を有効にすることで、ダイヤルダウンできます。 無効にすると、ライトマップからの光源は平坦になりますが、コストは安くなります。

![Unreal のモバイルマテリアル設定](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>前方シェーディングの調整

これらのオプションを選択すると、パフォーマンスが低下します。 パフォーマンスを最大にするためにオフにする必要があります。

![Unreal の事前シェーディングマテリアル設定](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>素材の透明度の設定

半透明のマテリアルがブルームまたは自由度の影響を受けないことを示します。 MR では両方の影響がまれであるため、この設定は既定でオンになっている必要があります。

![モバイル分離の透明度設定 (Unreal)](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>オプション設定

次の設定では、パフォーマンスが向上する場合がありますが、特定の機能が無効になっていることに注意してください。 問題の機能を必要としない場合にのみ、これらの設定を使用してください。

![Unreal のオプションのマテリアル設定](images/unreal-materials-img-06.jpg)

マテリアルに反射や光が不要な場合は、このオプションを設定するとパフォーマンスが大幅に向上する可能性があります。 内部テストでは、照明情報を提供すると同時に "unlit" の速度になります。

## <a name="best-practices"></a>ベスト プラクティス

以下は、資料に関連するベストプラクティスであるため、"設定" ではありません。

パラメーターを作成するときは、可能な限り "静的パラメーター" を使用することをお勧めします。 静的スイッチを使用すると、実行時のコストを発生させずに、素材の分岐全体を削除できます。 インスタンスは異なる値を持つことができるため、テンプレート化されたシェーダーを設定し、パフォーマンスを低下させることはできません。 ただし、これによって多くの順列が生成されるため、多くのシェーダーの再コンパイルが発生します。 マテリアル内の静的なパラメーターの数と、実際に使用される静的パラメーターの順列の数を最小限に抑えてください。 レンダリングマテリアルのパラメーターの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)を参照してください。

![マテリアル設定のベストプラクティス](images/unreal-materials-img-07.jpg)

素材のインスタンスを作成するときは、マテリアルインスタンスの **定数** を動的に使用するように設定する必要があります。 **Material Instance Constant** は、ランタイムの前に1回だけ計算する、インスタンス化された素材です。

コンテンツブラウザーを使用して作成された素材インスタンス ( **右クリック > Create Material instance** ) は、素材インスタンス定数です。 マテリアルインスタンス動的は、コードを使用して作成されます。 マテリアルインスタンスの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)を参照してください。

![Unreal での素材インスタンスの作成](images/unreal-materials-img-08.png)

素材/シェーダーの複雑さに注意してください。 [プラットフォームの統計] アイコンをクリックすると、さまざまなプラットフォームでの素材のコストを表示できます。 素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。

![Unreal での素材インスタンス動的設定の作成](images/unreal-materials-img-09.png)

シェーダーの複雑さの [表示モード](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)を使用して、シェーダーの相対的な複雑さを簡単に把握できます。

* 表示モードホットキー: Alt + 8
* コンソールコマンド: viewmode shadercomplexity

![Unreal の素材の複雑さ](images/unreal-materials-img-10.png)

## <a name="see-also"></a>関連項目
* [モバイル資料](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [表示モード](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [素材のインスタンス](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
