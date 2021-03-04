---
title: Unity での手と視点の追跡
description: Unity、ハンドジェスチャ、およびモーションコントローラーの2つの操作方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ジェスチャ、モーションコントローラー、unity、宝石、入力、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 8c1ab88358f4218fadce9b7a2a0dbd179b680eab
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759758"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity での手と視点の追跡

HoloLens 2 では、左手や視線の追跡など、いくつかの新機能と魅力的な機能が導入されました。

Unity の新機能を利用する最も簡単な方法は、MRTK を使用することです。 また、使用を開始する際に役立ついくつかのシーンもあります。

* [MRTK での手による作業の開始](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/hand-tracking.md)
* [MRTK での視線追跡の概要](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>MRTK の手や目などをサポートするビルディングブロック 

MRTK v2 には、開発を高速化するために役立つ一連の UI コントロールと構成要素が用意されています。

|  [ ![ ボタン](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md)[ボタン](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) | [ ![ 境界ボックス](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md)の[境界ボックス](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) | [ ![ 操作ハンドラー](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md)の[操作ハンドラー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| HoloLens2's を含むさまざまな入力メソッドをサポートするボタンコントロール | 3D 空間内のオブジェクトを操作するための標準 UI | 1人または2人の手でオブジェクトを操作するためのスクリプト |
|  [ ![ スレート](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md)[スレート](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) | [ ![ システムキーボード](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md)の[システムキーボード](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) | [ ![ 対話型](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md)[対話型](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) |
| 入力によるスクロールをサポートする2D スタイル平面 | Unity でシステムキーボードを使用するサンプルスクリプト  | 視覚的な状態とテーマのサポートを使用してオブジェクトを対話型するためのスクリプト |
|  [ ![ ソルバー](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) [ソルバー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) | [ ![ オブジェクトコレクション](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md)[オブジェクトコレクション](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) | [ ![ ツール](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md)ヒントの[ツールヒント](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) |
| タグ沿い、本文ロック、定数ビューサイズ、および表面吸着などのさまざまなオブジェクトの配置動作 | 3次元図形内のオブジェクトの配列をレイアウトするためのスクリプト | フレキシブルアンカー/ピボットシステムを使用した注釈 UI。モーションコントローラーとオブジェクトのラベル付けに使用できます。 |
|  [ ![ アプリバー](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) [アプリバー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) | [ ![ ポインター](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) [ポインター](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) | [ ![ 指先ビジュアライゼーション](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md)[指先の視覚化](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) |
| 境界ボックスの手動アクティブ化の UI | さまざまな種類のポインターについて | 指先での Visual affordance による直接的な相互作用の信頼性の向上 |
|  [ ![ 視線追跡: ターゲット選択](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md)の[視点の追跡: ターゲットの選択](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) | [ ![ 目の追跡: ナビゲーション](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md)の監視[: ナビゲーション](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) | [ ![ 目の追跡: ヒートマップ](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html)の[視線追跡: ヒートマップ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 視点、音声、手入力を組み合わせてシーン全体のホログラムをすばやく簡単に選択する | 見ている内容に基づいて、テキストを自動的にスクロールしたり、フォーカスされるコンテンツにズームしたりする方法について説明します。| アプリでユーザーが見ていることをログに記録し、読み込んで、視覚化する例 |

## <a name="example-scenes"></a>シーンの例

[このシーンの例](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)では、MRTK のさまざまな種類の相互作用と UI コントロールについて説明します。

その他の例については、「 **Assets/MixedRealityToolkit/デモ** フォルダー」にある [Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)を参照してください。

[![シーンの例](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/hand-interaction-examples.md)

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [空間マッピング](spatial-mapping-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [視線ベースの操作](../../design/eye-gaze-interaction.md)
* [HoloLens 2 上の視線追跡](../../design/eye-tracking.md)
* [視線入力とコミット](../../design/gaze-and-commit.md)
* [手 - 直接操作](../../design/direct-manipulation.md)
* [手 - ジェスチャ](../../design/gaze-and-commit.md#composite-gestures)
* [手 - ポイントとコミット](../../design/point-and-commit.md)
* [本能的な操作](../../design/interaction-fundamentals.md)
* [モーション コントローラー](../../design/motion-controllers.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 追跡](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
