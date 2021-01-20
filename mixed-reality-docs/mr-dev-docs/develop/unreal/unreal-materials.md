---
title: Unreal の素材に関する推奨事項
description: Unreal engine のマテリアルの概要。
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開発、マテリアル、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: bfe70e730c5fbd6e5d103737b03e76bfd0ab65f6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580798"
---
# <a name="material-recommendations-in-unreal"></a>Unreal の素材に関する推奨事項

使用する素材は、Unreal Engine でのプロジェクトの実行がどの程度適切であるかに直接影響します。 このページは、混合現実アプリケーションから最適なパフォーマンスを得るために使用する必要がある基本設定のクイックスタートとして機能します。

## <a name="using-customizeduvs"></a>CustomizedUVs の使用

素材に UV タイルを提供する必要がある場合は、テクスチャノードの UV を直接変更するのではなく、CustomizedUVs を使用します。 CustomizedUVs を使用すると、ピクセルシェーダーではなく、頂点シェーダーで UVs を操作できます。

![Unreal のマテリアル設定](images/unreal-materials-img-01c.png)

素材の詳細については、次のスクリーンショットの [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) とベストプラクティスの例を参照してください。

推奨される[ ![ 未 ](images/unreal-materials-img-01.png) 設定の資料での推奨資料の設定](images/unreal-materials-img-01.png#lightbox) 
 

推奨される[ ![ unreal ](images/unreal-materials-img-01b.png) 以外のマテリアルのセットアップでの推奨されるマテリアル以外の設定](images/unreal-materials-img-01b.png#lightbox) 
 

## <a name="changing-blend-mode"></a>Blend モードの変更

特に複雑な理由がない限り、blend モードを不透明に設定することをお勧めします。 マスクされた半透明な素材は低速です。 素材の詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)を参照してください。

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

次の設定では、パフォーマンスが向上する場合がありますが、特定の機能が無効になっていることに注意してください。 該当する機能が不要な場合にのみ、これらの設定を使用してください。

![Unreal のオプションのマテリアル設定](images/unreal-materials-img-06.jpg)

マテリアルに反射や光が不要な場合は、このオプションを設定するとパフォーマンスが大幅に向上する可能性があります。 内部テストでは、照明情報を提供しながら、"unlit" のように高速です。

## <a name="best-practices"></a>ベスト プラクティス

以下は、資料に関連するベストプラクティスであるため、"設定" ではありません。

パラメーターを作成するときは、可能な限り "静的パラメーター" を使用することをお勧めします。 静的スイッチを使用すると、実行時のコストを発生させずに、素材の分岐全体を削除できます。 インスタンスは異なる値を持つことができるため、パフォーマンスが失われることなく、テンプレート化されたシェーダーを設定できます。 欠点は、シェーダーの再コンパイルの原因となるいくつかの順列が作成されることです。 マテリアル内の静的なパラメーターの数と、使用される静的パラメーターの順列の数を最小限に抑えてください。 レンダリングマテリアルのパラメーターの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)を参照してください。

![マテリアル設定のベストプラクティス](images/unreal-materials-img-07.jpg)

素材のインスタンスを作成するときは、マテリアルインスタンスの **定数** を動的に使用するように設定する必要があります。 **Material Instance Constant** は、実行前に1回だけ計算する、インスタンス化された素材です。

コンテンツブラウザーを使用して作成された素材インスタンス (**右クリック > Create Material instance**) は、素材インスタンス定数です。 マテリアルインスタンス動的は、コードを使用して作成されます。 マテリアルインスタンスの詳細については、 [Unreal Engine のドキュメント](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)を参照してください。

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
