---
title: Unreal のパフォーマンスに関する推奨事項
description: Unreal の Mixed Reality アプリで最適なパフォーマンスを得るための推奨事項
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, パフォーマンス, 最適化, 設定, ドキュメント
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699290"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal のパフォーマンスに関する推奨事項

## <a name="overview"></a>概要

この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unreal Engine に固有の学習に焦点を当てています。 続行する前に、アプリケーションのボトルネック、Mixed Reality アプリの分析とプロファイリング、および一般的なパフォーマンスの修正について確認することをお勧めします。

## <a name="recommended-unreal-project-settings"></a>推奨される Unreal プロジェクト設定を使用する
以下の各設定は、 **[編集] > [プロジェクトの設定]** にあります。

1. Mobile VR レンダラーの使用:
    * **[プロジェクト]** セクションまでスクロールし、 **[ターゲット ハードウェア]** を選択して、ターゲット プラットフォームを **[モバイル/タブレット]** に設定します。

![モバイル ターゲット設定](images/unreal/performance-recommendations-img-01.png)

2. 前方レンダラーの使用: 
    * Mixed Reality には、既定の遅延レンダリング パイプラインよりもこの機能の方がはるかに適しています。 その理由は主に、個別にオフにできる機能の数にあります。 
    * 詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)を参照してください。

![前方レンダリング](images/unreal/performance-recommendations-img-04.png)

3. 頂点フォグの無効化: 
    * 頂点フォグでは、多角形の各頂点にフォグ計算を適用し、その結果を多角形の面全体で補間します。 ゲームでフォグを使用しない場合は、この設定を選択してフォグを無効にし、シェーディングのパフォーマンスを向上させる必要があります。

![頂点フォグのオプション](images/unreal/performance-recommendations-img-05.png)

4. オクルージョン カリングの無効化:
    * **[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[カリング]** セクションを展開して、 **[オクルージョン カリング]** をオフにします。
        + レンダリングされる詳細なシーンのオクルージョン カリングが必要な場合は、 **[エンジン] > [レンダリング]** で **[ソフトウェア オクルージョン カリングのサポート]** を有効にすることをお勧めします。 これにより、Unreal の作業は CPU 上で実行され、HoloLens 2 でのパフォーマンスが低い GPU オクルージョン クエリを回避できます。
    * モバイル デバイスの GPU でオクルージョン カリングを行うと処理速度が低下します。 一般に、GPU では主にレンダリングを行う必要があります。 オクルージョンによってパフォーマンスが向上すると思われる場合は、代わりにソフトウェア オクルージョンを有効にしてください。 多数の描画呼び出しによって既に CPU の負荷が大きくなっている場合、ソフトウェア オクルージョンを有効にするとパフォーマンスが低下する可能性があることに注意してください。

![オクルージョン カリングの無効化](images/unreal/performance-recommendations-img-02.png)

    
5. 深度ステンシルの無効化:
    * この機能には追加のパスが必要になるため、処理速度が低下します。 Unreal では、透明度を使用した場合も処理が遅くなります。 詳細については [Unreal のドキュメント](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)を参照してください。

![深度ステンシル](images/unreal/performance-recommendations-img-06.png)

6. モバイル マルチビューの使用:
    * **[エンジン]** セクションまでスクロールし、 **[レンダリング]** を選択し、 **[VR]** セクションを展開して、 **[インスタンス化ステレオ]** と **[モバイル マルチビュー]** の両方を有効にします。 モバイル HDR をオフにする必要があります。

![VR レンダリング設定](images/unreal/performance-recommendations-img-03.png)

7. カスケードされたシャドウ マップの削減: 
    * シャドウ マップの数を減らすと、パフォーマンスが向上します。 明らかに品質が低下しない限り、一般にこれは 1 に設定する必要があります。 

![カスケードされたシャドウ マップ](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>オプション設定

> [!NOTE]
> 次の設定を行うとパフォーマンスが向上する可能性がありますが、代わりに特定の機能が無効になります。 該当する機能が不要な場合にのみ、これらの設定を使用してください。

1. モバイル シェーダーの順列の削減
    * ライトがカメラとは無関係に移動しない場合は、この値を問題なく 0 に設定できます。 主な利点は、Unreal で複数のシェーダー順列をカリングし、シェーダーのコンパイルを高速化できることです。

![モバイル シェーダーの順列の削減](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>関連項目
* [Unreal Engine モバイルのパフォーマンス ガイドライン]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)